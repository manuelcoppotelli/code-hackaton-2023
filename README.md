# VMware Explore Code Hackaton 2023

## Slides

see [`slides.md`](/slides.md)

## Demo

### Requirements

```sh
brew tap vmware-tanzu/carvel
brew install kapp kbld ytt kctrl imgpkg vendir
```

### Show

```sh
MSG=terminal go run src/app.go

kubectl port-forward services/demo-deploy 8080

kapp deploy -a demo-app -f manifests/

kbld -f manifests/ -f config.yml

kbld -f manifests/ -f config.yml | kapp deploy -a demo-app -c -y -f-

ytt -f manifests/ -v msg=cli

ytt -f manifests/ -v msg=cli | kbld -f config.yml -f- | kapp deploy -a demo-app -c -y -f-

ytt -f manifests/ -f envs/dev/values.yml | kbld -f config.yml -f- | kapp deploy -a demo-app -c -y -f-
```
