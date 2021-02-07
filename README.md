Taken from Manjaro forums. This contains the proper files to compile Nvidia Drivers 340 into Kernels 5.4 and 5.10. So far I tested this on 5.4, 5.9 (so far no problems at all) and 5.10.

In order to do this, your system needs development tools. Those can be installed with the following command: sudo pacman -S git base-devel

Kernel headers are going to be needed as well sudo pacman -S $(mhwd-kernel -li | grep '*' | cut -d ' ' -f5 | awk '{print $0,"-headers"}' | sed s'/ //'g)

This is going to install the proper headers on your kernel/s

Here are the source for the drivers

git clone https://gitlab.manjaro.org/packages/extra/nvidia-340xx-utils.git

git clone https://gitlab.manjaro.org/packages/multilib/lib32-nvidia-340xx-utils.git

git clone https://github.com/philmmanjaro/nvidia-340xx-dkms.git

Then compile all packages with makepkg:

cd nvidia-340xx-utils && makepkg -si cd ../lib32-nvidia-340xx-utils && makepkg -si cd ../nvidia-340xx-dkms && makepkg -si

With this you will have 340xx driver, even Manjaro officially dropped it.
