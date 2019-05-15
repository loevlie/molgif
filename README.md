# molgif

create smooth gifs of rotating molecules

Requirements

- ase
- matplotlib
- ImageMagick (command line tools must be installed)

![C60](gifs/C60.gif)

## Examples

### Automatically rotate molecule for better view

    import molgif
    import ase.build

    # load in molecule (ase.Atoms object)
    molecule = ase.build.molecule('biphenyl')

    # specify save path
    save_path = 'biphenyl.gif'

    # create rotating gif with rot_gif function
    molgif.rot_gif(molecule, save_path, auto_rotate=True)

![biphenyl](gifs/biphenyl.gif)

### Adjust loop time and FPS

    # time to complete one rotation (seconds)
    loop_time = 2

    # frames per second
    fps = 60

    molgif.rot_gif(molecule, save_path, auto_rotate=True,
                   loop_time=loop_time, fps=fps)

![biphenyl-2s-looptime](gifs/biphenyl-2s-looptime.gif)

### Turn off bonds and scale atomic sizes

    molgif.rot_gif(molecule, save_path, auto_rotate=True,
                   add_bonds=False, scale=0.9)

![biphenyl-no-bonds](gifs/biphenyl-no-bonds.gif)

### Visualize charges and include a colorbar

    import random

    # random charges [-1, 1]
    chgs = [-1 + 2 * random.random() for i in molecule]

    molecule.set_initial_charges(chgs)

    molgif.rot_gif(molecule, save_path, auto_rotate=True,
                   use_charges=True)

![biphenyl-charges](gifs/biphenyl-charges.gif)
