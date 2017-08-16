# Supported tags and respective `Dockerfile` links

- [`alpine-3.6`, `alpine`, `latest` (*Dockerfile*)](https://github.com/RPDiep/sftp/blob/master/Dockerfile) [![](https://images.microbadger.com/badges/image/rpdiep/sftp.svg)](http://microbadger.com/images/rpdiep/sftp "Get your own image badge on microbadger.com")

# Securely share your files

Easy to use SFTP ([SSH File Transfer Protocol](https://en.wikipedia.org/wiki/SSH_File_Transfer_Protocol)) server with [OpenSSH](https://en.wikipedia.org/wiki/OpenSSH).
This is an automated build linked with the [alpine](https://hub.docker.com/_/alpine/) repositories.

# Usage

- Required: 
Environment variables `user`, `uid` and either `pwhash` or `auth_keys`

# Example

```
docker run -p 22:22 -d RPDiep/sftp -e "user=foo" -e "pwhash=<password hash>" -e "uid=1000"
```

# Logging in

The OpenSSH server runs by default on port 22, and in this example, we are
forwarding the container's port 22 to the host's port 2222. To log in with the
OpenSSH client, run: `sftp -P 2222 foo@<host-ip>`

Tip: you can use [RPDiep/makepasswd](https://hub.docker.com/r/RPDiep/makepasswd/) to generate encrypted passwords:  
`echo -n "your-password" | docker run -i --rm RPDiep/makepasswd --crypt-md5 --clearfrom=-`

## Logging in with SSH keys

Simply fill the `auth_keys` environment variable with a base64 encoded string containing the `authorized_keys` file content

