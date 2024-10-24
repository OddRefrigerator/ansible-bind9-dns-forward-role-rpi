# Ansible Role: Bind9 DNS Forwarder for Raspberry Pi

This Ansible role configures a Bind9 DNS server as a DNS forwarder on Raspberry Pi. It's designed to help set up and manage a simple DNS forwarding service, directing DNS queries from the local network to upstream DNS servers for resolution.

## Features

- **Automated Setup:** Fully automated configuration of Bind9 on a Raspberry Pi using Ansible.
- **DNS Forwarding:** Set up Bind9 as a DNS forwarder, forwarding DNS requests to specified upstream DNS servers.
- **Customizable:** Ability to customize forwarder addresses, domain configurations, and other DNS settings.
- **Lightweight:** Minimal resource consumption, ideal for Raspberry Pi devices running in small networks.

## Requirements

- Raspberry Pi with a compatible OS (e.g., Raspberry Pi OS).
- Ansible installed on the control machine.
- Root or sudo privileges on the Raspberry Pi.

## Role Variables

Available variables for customization are located in the `defaults/main.yml` file. Below are the key variables:

```yaml
# Upstream DNS servers for forwarding requests
dns_forwarders:
  - "8.8.8.8"
  - "8.8.4.4"

# The interface Bind9 will listen on
bind_interfaces:
  - "eth0"

# DNS domain options (optional)
dns_domain: "example.com"
```

You can override these variables by defining them in your playbook or providing them in your inventory.

## Example Playbook

Here’s a basic playbook to apply this role:

```yaml
---
- hosts: raspberrypi
  become: true
  roles:
    - role: ansible-bind9-dns-forward-role-rpi
      vars:
        dns_forwarders:
          - "1.1.1.1"
          - "9.9.9.9"
        bind_interfaces:
          - "eth0"
        dns_domain: "myhome.local"
```

## Installation

To install and use this role:

1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/OddRefrigerator/ansible-bind9-dns-forward-role-rpi.git
   ```

2. Include the role in your Ansible playbook.

3. Run the playbook to configure the Bind9 DNS forwarder on your Raspberry Pi:
   ```bash
   ansible-playbook -i inventory my-playbook.yml
   ```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Feel free to submit issues or open a pull request if you have any improvements or fixes.

### Steps for Contribution

1. Fork the repository.
2. Create a new branch for your feature or fix:
   ```bash
   git checkout -b feature-name
   ```
3. Commit your changes:
   ```bash
   git commit -m "Description of your feature or fix"
   ```
4. Push your branch:
   ```bash
   git push origin feature-name
   ```
5. Open a pull request with a detailed explanation of your changes.

## Author

This role was created by [OddRefrigerator](https://github.com/OddRefrigerator).

## Contact

For any inquiries or issues, feel free to open an issue on GitHub or contact the repository owner.
