---
marp: true
theme: uncover
_class: invert
---

<!-- header: VMware {code} Hackaton 2023 -->
<!-- footer: slides made with 🍻, 🤬 and [marp.app](https://marp.app) -->

# VMware Tanzu

## tailored for Devs (team 7)

Manuel Coppotelli

---

# Why "tailored for devs" ?

* Developers need a palygroud...
* ... not too much different that produciton
* Tanzu locally is not feasible
* ... so let's make it!!

---

# General idea

1. developer on its local machine can run its code (prossibly *in* container)
2. developer can `git push` its work without (many) changes
3. (hopefully) the platform would run the software at scale

---

# Ingredients

1. (_opinionated_) directory structure

```text
├── config.yml
├── envs
│   ├── dev
│   │   └── values.yml
│   └── stage
│       └── values.yml
├── manifests
│   ├── deployment.yml
│   ├── rbac.yml
│   └── service.yml
└── src
    ├── Dockerfile
    └── app.go
```

---

# Ingredients (cont'd)

2. The right combination of tools

```bash
ytt -f manifests/ -f envs/stage/values.yml \
    | kbld -f config.yml -f- \
    | kapp deploy -a demo-app -c -y -f-
```

---

# Demo

_🙏Please demo God be kind with me 🙏_

---

# Output

1. developer on its local machine can run its code (prossibly *in* container) ✅
2. developer can `git push` its work without (many) changes ✅
3. (hopefully) the platform would run the software at scale ⚠️⚙️

> Would have introduced `imgpkg` tool and `kapp controller` to bring into actual Tanzu

---

# Lesson learned

* Making quick slides (thank you markdown!)
* Everything can be done with the right amount of beer
* **IPA** is what can be generally considered _"beer"_

_and last but not least..._

* Carvel suite (kapp, kbld, ytt, kctrl, imgpkg, vendir) is amazing!

---

# Thank you

All the material available on Github:

<https://github.com/manuelcoppotelli/code-hackaton-2023>
