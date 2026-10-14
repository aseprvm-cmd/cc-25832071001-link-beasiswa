# Manual Deployment M03

## Application Path
`/srv/cc-m03`

## Service
`cc-m03.service` (systemd)

## Backend
`127.0.0.1:8000` (Gunicorn)

## Public Endpoint
`http://85.211.252.8/`

## Update Procedure

```bash
cd /srv/cc-m03
git pull
source .venv/bin/activate
python -m pip install -r requirements.txt
sudo systemctl restart cc-m03
sudo systemctl status cc-m03 --no-pager
curl -fsS http://127.0.0.1:8000/health
curl -fsS http://127.0.0.1/health
```

## Logs

```bash
sudo journalctl -u cc-m03 -n 50 --no-pager
sudo journalctl -u caddy -n 50 --no-pager
```

## Rollback

```bash
git log --oneline --decorate -10
git checkout m03
sudo systemctl restart cc-m03
git switch main
```
