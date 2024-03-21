# Ansible Role: Point DHCP to PXE

An ansible role that configures a DHCP server to point to a PXE Server.

## Requirements

No specific requirements, but the target system should have a DHCP server installed and configured.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
dhcp_to_pxe_tftp_root: /mnt/extstorage/tftp
```

The root directory of the TFTP server. This is where the PXE server will store the boot files.

```yaml
dhcp_to_pxe_bootfile: netboot.xyz.efi
```

The boot file that the DHCP server will point to. This is the image that will be served to the PXE clients.

```yaml
dhcp_to_pxe_server_address: '127.0.0.1'
```

The IP address of the PXE server. This is `localhost` by default because most PXE servers are on the same machine as the DHCP server.

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: dhcp-to-pxe
      vars:
        dhcp_to_pxe_tftp_root: /mnt/usb/tftp
        dhcp_to_pxe_bootfile: netboot.xyz.efi
        dhcp_to_pxe_server_address: '192.168.1.69'
      become: true
```

## License

MIT
