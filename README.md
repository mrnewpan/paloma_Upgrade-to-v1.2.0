## Upgrade-to-v1.2.0
```
sudo systemctl stop palomad
```

### upgrade paloma
```
cd || return
rm -rf paloma
git clone https://github.com/palomachain/paloma.git
cd paloma || return
git checkout v1.2.0
make install
sudo mv -f $HOME/go/bin/palomad /usr/local/bin/palomad
palomad version # v1.2.0
```
```
sudo systemctl daemon-reload
sudo systemctl enable palomad
sudo systemctl enable pigeond
sudo systemctl start pigeond
sudo systemctl start palomad
```
### Check logs
```
sudo journalctl -u palomad -f --no-hostname -o cat
```
```
sudo journalctl -u pigeond -f --no-hostname -o cat
```
### Check synchronization
```
palomad status 2>&1 | jq .SyncInfo.catching_up
```
