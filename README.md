# Gitlab-Exiftool-RCE
RCE Exploit for Gitlab &lt; 13.10.3
- GitLab Workhorse will pass any file to ExifTool. The current bug is in the DjVu module of ExifTool.
- Anyone with the ability to upload an image that goes through the GitLab Workhorse could achieve RCE via a specially crafted file

## Usage
```
python3 exploit.py -u root -p root -c "command here" -t http://gitlab.example.com
```

## Environment
- Tested on Gitlab 13.10.2 Community Edition
- Building your own test environment :
```
export GITLAB_HOME=/srv/gitlab

sudo docker run --detach \
  --hostname gitlab.example.com \
  --publish 443:443 --publish 80:80 \
  --name gitlab \
  --restart always \
  --volume $GITLAB_HOME/config:/etc/gitlab \
  --volume $GITLAB_HOME/logs:/var/log/gitlab \
  --volume $GITLAB_HOME/data:/var/opt/gitlab \
  gitlab/gitlab-ce:13.10.2-ce.0
 ```

## Credits
- https://hackerone.com/reports/1154542 : vakzz
- https://devcraft.io/2021/05/04/exiftool-arbitrary-code-execution-cve-2021-22204.html

## Exploit-DB
- Soon
