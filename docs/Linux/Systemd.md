# systemd

## Basic Usage

```bash
# Start the service
systemctl start SERVICE_NAME

# Stop the service
systemctl stop SERVICE_NAME

# Check the status of service
systemctl status SERVICE_NAME

# Restart(Stop and Start) the Service
systemctl restart SERVICE_NAME

# Reload(The service may not stop) the service
systemctl reload SERVICE_NAME

# Start the service automatically when boot
systemctl enable SERVICE_NAME

# Disable start the service when boot
systemctl disable SERVICE_NAME
```
