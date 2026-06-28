tasks:
⁃ name: Run apt-get update and upgrade all packages ansible.builtin.apt: update_cache: yes upgrade: dist cache_valid_time: 3600
name: Check if a reboot is required ansible.builtin.stat: path: /var/run/reboot-required register: reboot_required_file,
nane: Reboot the container if required ansible.builtin.reboot: msg: "Rebooting container to apply updates" reboot_timeout: 180 when: reboot required file.stat.exists
