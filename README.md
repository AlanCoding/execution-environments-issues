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

#### Verified Solutions

Two options are noted in comments.
 - Use docker instead of podman (see `env/settings`)
 - Set the play variable `ansible_remote_tmp` to a location inside the volume

#### Failed Solutions

Adding:

```
"ANSIBLE_LOCAL_TEMP": "/runner"
```

to `env/envvars` has not worked.

It seems to be ignored, and continues to use the `/root/` folder.
