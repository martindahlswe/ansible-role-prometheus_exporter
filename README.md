# Ansible Role: Prometheus Exporter

This Ansible role installs and manages Prometheus exporters downloaded from GitHub. It sets them up as systemd services.

## ✅ Tested Exporters

- [speedtest-exporter](https://github.com/MiguelNdeCarvalho/speedtest-exporter)
- [prometheus-pve-exporter](https://github.com/prometheus-pve/prometheus-pve-exporter)
- And more!

## 📦 Role Variables

Define exporters in your playbook or inventory:

```yaml
exporters:
exporters:
  - name: speedtest
    method: manual
    repo: https://github.com/MiguelNdeCarvalho/speedtest-exporter.git
    src_dir: /opt/speedtest-exporter
    user: speedtest_exporter

  - name: pve
    github_repo: prometheus-pve/prometheus-pve-exporter
    binary_name: pve_exporter
    port: 9221
    args: "--pve-token-name prometheus --pve-token-value <your_token> --pve-host https://your.pve.host"
```

## 🚀 Example Playbook

```yaml
- hosts: all
  become: true
  roles:
    - role: prometheus_exporter
```

## 🧪 Requirements

- Ansible 2.9+
- Systemd-based Linux (Ubuntu, Debian)

## 📝 License

MIT
