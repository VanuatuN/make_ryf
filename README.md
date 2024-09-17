## Generate RYF data files


# On Leonardo assume to create and activate virtual environment


First start up an interactive job on Gadi to get enough memory:
In my case I do the following:

```bash
source ~/cosimaenv/bin/activate
```

The python .cgf file in the ~/cosimaenv/pyvenv.cfg looks as:

```bash
14:45 $ more ~/cosimaenv/pyvenv.cfg 
home = /leonardo/prod/spack/5.2/install/0.21/linux-rhel8-icelake/gcc-8.5.0/python-3.11.6-i5k3c6ggftqkzgqyymfbkynpgm2lgjtd/bin
include-system-site-packages = false
version = 3.11.6
executable = /leonardo/prod/spack/5.2/install/0.21/linux-rhel8-icelake/gcc-8.5.0/python-3.11.6-i5k3c6ggftqkzgqyymfbkynpgm2lgjtd/bin/python3.11
command = /leonardo/prod/spack/5.2/install/0.21/linux-rhel8-icelake/gcc-8.5.0/python-3.11.6-i5k3c6ggftqkzgqyymfbkynpgm2lgjtd/bin/python -m venv ~/cosimaenv
```


Also probably for some modules it is requiered to do load **spack module** (e.g. for ncview)

```bash
module load spack
```

Then if some packages are missing, just do 

```bash
pip install package
```

This script only does RYF for 1990_1991 year, as it has been shown as optimal year for RYS ( 


----- THIS PART OF THE README HAS NOT BEEN MODIFIED ------

```bash
qsub -I -X -P v45 -q express -l mem=32GB -l storage=gdata/hh5+gdata/qv56+gdata/ik11+gdata/ua8
```

leonardo analogue is likely ??
salloc --account=v45 --partition=express --mem=32G --export=ALL --gres=gdata:hh5,gdata:qv56,gdata:ik11,gdata:ua8 --x11
salloc --account=/leonardo_scratch/fast/ICT24_MHPC/ntilinin/INPUT

Then run the following to create the May-May repeat year forcings

```bash
module use /g/data3/hh5/public/modules
module load conda/analysis27

python make_ryf.py
```

