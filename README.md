# singularity-docker-fedora30-brave
fedora30 container to run brave (at library://tru/default/f30-brave)


Running without installation:
```
singularity run  -B /run library://tru/default/f30-brave
```
Building:
```
sudo singularity build singularity-docker-fedora30-brave.sif  Singularity
```
Download and rename:
```
singularity pull --name singularity-docker-fedora30-brave.sif library://tru/default/f30-brave
```
Running with a separate $HOME  (here ~/singularity.d/home/singularity-docker-fedora30-brave)
```
mkdir -p  ~/singularity.d/home/singularity-docker-fedora30-brave
singularity run  -B /run  -H ~/singularity.d/home/singularity-docker-fedora30-brave singularity-docker-fedora30-brave.sif
```
Upgrading on the fly by allowing the container to write to /your/choice/of/path (tagged >=2019-08-26)
```
mkdir /your/choice/of/path
singularity run  -B /run -B /your/choice/of/path:/opt/brave.com library://tru/default/f30-brave
```
if you don't use that feature, it will just run the embedded version
