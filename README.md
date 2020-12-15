### Execution Environment Container Permission Issues

This is to share `ansible-runner` private data directory inputs to replicate
issues.

```
ansible-runner run -p get_url.yml . -vvv
```

Important detail from that failure:

> Failed to replace file: /root/.ansible/tmp/ansible-tmp-1608050130.4774451-24-182673759779840/tmphrbsynsq to
> /runner/ansible-builder.zip: [Errno 13] Permission denied: b'/runner/.ansible_tmpoqn81kjoansible-builder.zip'

This is another example that should produce a similar result:

```
ansible-runner run -p blockinfile.yml . -vvv
```
