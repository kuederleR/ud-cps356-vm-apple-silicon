# Running The UD CPS356 VM on Apple Silicom
A compilation of files distilled for apple M-series macs to run the University of Dayton CPS356 course virtual machine.
### Downloading the OVM Files
To download pre-converted files, run the command:
```bash
git clone https://github.com/kuederleR/ud-cps356-vm-apple-silicon.git 
```

### Launch the VM
Navigate to the VM directory:
```bash
cd ud-cps356-vm-apple-silicon
```

Launch the VM: You will use this command to launch the VM in the future.
```bash
qemu-system-x86_64 -m 4G -smp 4 -drive file=CPS-356-disk.qcow2,format=qcow2 -boot c -cpu qemu64 -accel tcg,thread=multi -vga virtio
```

## Converting to OVM for ARM64
1. **Launch Original VM**:
First, the VM must be imported to VMWare Workstation on an x86 machine (see course instruction).

2. **Export in OVF Format**:
Once the VM is available in Workstation, select it from the Workstation manager, select `File > Export to OVF...`. Follow the prompts on screen to create the OVF file, the virtual disk file, and a checksum file. In the export location selected, you will see `.ovf, .vmdk, .mf` files. Transfer these files to an Apple Silicon Mac and proceed with the following steps. 

Move the transferred files to a permanent location where you will launchy your VM from in the future. 

3. **Convert the .vmdk Disk**:
In your VM directory on your mac, run the command:
```bash
qemu-img convert -f vmdk -O qcow2 <disk-file-name>.vmdk CPS-356-disk.qcow2 # Replace <disk-file-name> with the name of your .vmdk file.
```

4. **Launch the VM**: See [Launch the VM](#launch-the-vm).
