# singularity-docker-fedora30-brave
fedora30 container to run brave


Running without installation:
```
singularity run library://tru/f30-brave
```
Building:
```
sudo singularity build singularity-docker-fedora30-brave.sif  Singularity
```
Download and rename:
```
singularity pull --name "singularity-docker-fedora30-brave" library://tru/f30-brave
```
Running with a separate $HOME 
```
mkdir -p  ~/singularity.d/home/singularity-docker-fedora30-brave
singularity run -H  ~/singularity.d/home/singularity-docker-fedora30-brave singularity-docker-fedora30-brave.sif
```
