<!--
    DO NOT MANUALLY EDIT THIS FILE
    THIS FILE IS AUTOMATICALLY GENERATED WITH resilient-circuits codegen
-->

# Example: Launch Tenable.io Scan by IP

## Function - Tenable.io Assets

### API Name
`tenable_io_assets`

### Output Name
`None`

### Message Destination
`fn_tio_assets`

### Pre-Processing Script
```python

inputs.incident_id = incident.id
inputs.artifact_id = artifact.id
inputs.tio_operation_type = 'scan'
inputs.tio_ip_addr = artifact.value

```

### Post-Processing Script
```python

scan_name = results.get('scan_name')
scan_uuid = results.get('scan_uuid')
scan_url = results.get('scan_url')
if scan_uuid:
  hyperlinked_text = 'Tenable.io scan initiated. Scan name: {0}, Scan uuid: <b><a href="{2}">{1}</a></b>'.format(scan_name, scan_uuid, scan_url)
  incident.addNote(helper.createRichText(hyperlinked_text))

```

---

