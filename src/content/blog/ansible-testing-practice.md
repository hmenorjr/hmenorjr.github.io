---
title: "Ansible Testing Practice"
description: "DevOps is already part of my tasks as an experienced Software Engineer and Web Developer. Here are some practice to test your Ansible script."
pubDate: "Oct 25 2023"
heroImage: "/ansible_play_meme.png"
badge: "latest"
---

Because most of my experience revolves around development, I wondered how would one test the Ansible script and works as expected?

Here are some steps and techniques to help you test your Ansible scripts.

## Syntax Check

Before anything else, you should always start by checking the syntax of your Ansible scripts. You can use the `ansible-playbook` command with the `--syntax-check` flag to identify any syntax errors.

```bash
ansible-playbook your_playbook.yml --syntax-check
```

## Dry Run

Use the `--check` flag with `ansible-playbook` to perform a dry run. This checks what would be changed without actually making any changes.

```bash
ansible-playbook your_playbook.yml --check
```

## Verbose Mode

Increase verbosity using the `-v` or `-vv` flags to get more detailed output, which can help you identify issues.

```bash
ansible-playbook your_playbook.yml -vv
```

## Limit to a Subset

Use the `--limit` option to target a specific subset of hosts, which can be useful for testing on a smaller scale.

```bash
ansible-playbook your_playbook.yml --limit hostname
```

## Use Ansible's Debug Module

Insert `debug` tasks at different points in your playbook to print variable values and information for troubleshooting.

```yaml
- name: Debug Information
   debug:
     var: your_variable

```

## Use the --list-hosts Option

This option lists all the hosts that Ansible would run against. It's useful for verifying the hosts that Ansible is targeting.

```bash
ansible-playbook your_playbook.yml --list-hosts
```

## Check the Output

Well, after running your playbook, you can carefully review the output for any errors, warnings or unexpected behavior.

## Rollback Plan

When making changes that could potentially disrupt your systems. Ensure you have a rollback plan in place which you can use if something goes wrong during the playbook execution. Kind of the same when you're updating databases.

## Run in a Testing Environment

Another good practice to first test your playbooks in a non-production environment or on a subset of your infrastructure to minimize risks. I think this is already given if you've been developing apps for quite some time.

## Use Ansible Modules in Check Mode

Some Ansible modules support check mode. You can add the `check_mode: yes` parameter to tasks using such modules. This way, Ansible will only check if the desired state is achieved without making any changes.

```yml
- name: Ensure a file exists (check mode)
  ansible.builtin.file:
    path: /path/to/file
    state: touch
  check_mode: yes
```

## Automated Testing

Consider integrating Ansible testing into your CI/CD pipeline using tools like Molecule or Ansible's built-in `ansible-test`.

## Manual Testing

Finally, manual testing is crucial. Validate that the desired changes have been applied correctly and that your systems are functioning as expected. But, as much as possible use this as your last option.

## Final Thoughts

These are just some of the stuff I searched since I feel like I'm still "raw" when it comes to Software Engineering for DevOps. Any more you could add?

## Support

Do you like this? Consider donating or subscribing for support.

[![Buy me a coffee](/buy_me_a_coffee.webp)](https://ko-fi.com/hmenorjr)
