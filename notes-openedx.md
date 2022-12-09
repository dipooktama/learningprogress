# A Note for OpenEDX Development using Devstack

## The steps

1. `git clone` the [devstack repo](https://github.com/openedx/devstack#getting-started). It will be named as `devstack`.
2. `cd` to that dir
3. make a virtual environment at that dir by using 

```
virtualenv .
```` 
(*make sure that you had `virtualenv` already installed with `pip` and it's added to your system path*)

4. activate the _venv_ by using 
```
source .bin/activate
```

5. install the required files by using 
```
make requirements
```
6. and then 

```
make dev.clone
```

7. because we are using the `nutmeg` release, set the env var of `OPENEDX_RELEASE` to `nutmeg.master` first
```
export OPENEDX_RELEASE="nutmeg.master"
```

8. then checkout to that version release
```
git checkout open-release/nutmeg.master
```

9. then use this command below
```
make dev.checkout
```

10. and then pull the image with this
```
make dev.pull.large-and-slow
```
if you are only want a certain service(s), you could follow this [guide](https://edx.readthedocs.io/projects/open-edx-devstack/en/latest/workflow.html#multiple-services)
or simply using `make dev.pull.<serviceName1>+<serviceName2>`

11. then
```
make dev.provision
```

12. then start the service using `up`
```
make dev.up.large-and-slow
```
or `make dev.up.<serviceName1>`

---

if you need a shell access, you can run:
```
make dev.shell.<serviceName>
```
