# ServoShutter
 Servomotor based shutter mechanism controlled by STM Nucleo L432KC

## PREREQUSITES
- micro USB cable to connect microcontroller
- DC power supply ()
- you need to know the full name of device which windows sees (look at 'Full name' section)

## FULL NAME
To obtain full device name you can run a python script below (for Windows systems). Look for devices manufacured by STMicroelectronics.

```python
import serial.tools.list_ports

def list_connected_devices():
    devices = serial.tools.list_ports.comports()
    if not devices:
        print("No devices found.")
        return

    print(f"{'Port':<10} {'VID':<10} {'PID':<10} {'HWID':<25} {'Description':<30}")
    print("-" * 80)

    for device in devices:
        port = device.device
        vid = f"{device.vid:04X}" if device.vid else "N/A"
        pid = f"{device.pid:04X}" if device.pid else "N/A"
        hwid = device.hwid if device.hwid else "N/A"
        
        print(f"{port:<15} {vid:<15} {pid:<10} {hwid:<35}")

if __name__ == "__main__":
    list_connected_devices()
```

## INSTALLATION AND USAGE

When you succesfully connect and obtain FULL NAME, you can now edit the `devices.ini` and `local_devices.ini` files with entries from `ini_files_entries.txt` and edit `ServoShutter.py` by replacing the existing full name of the device as a class attribute.

After that you should be able to operate servo via PyLUMS with a widget or console commands.
