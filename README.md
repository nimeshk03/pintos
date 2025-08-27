# Pintos Interactive Shell

**Course**: CS2042 - Operating Systems  
**Student**: Nimesh Kulatunga (230350D)  
**Institution**: University of Moratuwa  
**Academic Year**: 2024/2025

## Project Overview

This project implements an interactive kernel-level shell for the Pintos operating system. Pintos is a teaching operating system for x86 architecture, originally developed at Stanford University by Ben Pfaff and others. It's challenging but manageable, small but realistic enough to understand OS concepts in depth, and capable of running on x86 machines and simulators including QEMU, Bochs, and VMware Player.

The upstream source for this project comes from https://github.com/kavienanj/pintos.git, which is based on the original Pintos framework.

## Features Implemented

### Week 1: Interactive Shell
- **Kernel-level shell** that runs when no command line arguments are provided
- **Seven interactive commands**:
  - `whoami` - Display student name and index number
  - `shutdown` - Shutdown Pintos OS and exit QEMU emulator
  - `time` - Display seconds elapsed since Unix epoch (January 1, 1970)
  - `ram` - Display total RAM available to the OS
  - `thread` - Display current thread statistics
  - `priority` - Display current thread priority
  - `exit` - Exit the interactive shell
- **Input handling** with backspace support for command editing
- **Command validation** with helpful error messages for unknown commands
- **Professional interface** with welcome banner and clear prompt (`CS2042>`)

## Technical Implementation

### Architecture
- **Location**: `src/threads/init.c` - Main kernel initialization file
- **Integration Point**: Replaces the TODO section in `pintos_init()` function
- **Input System**: Uses `devices/input.c` for character input via `input_getc()`
- **Output System**: Uses kernel printf functions for display
- **System Information**: Accesses RTC, memory, and thread subsystems

### Key Functions
- `interactive_shell()` - Main shell loop
- `read_line()` - Input handling with backspace support
- `shell_*()` functions - Individual command implementations
- Integration with existing Pintos kernel subsystems

### Build System
- Uses standard Pintos Makefile system
- No additional files required (as per assignment requirements)
- Compiles with existing kernel build process

## Development Environment

### Docker Setup
```bash
# Mount project directory for persistent changes
docker run -it --rm --mount type=bind,source="C:\Users\nimes\OneDrive\Engineering\Semester 3\OS\PintOS\pintos",target=/pintos pintos
```

### Build Process
```bash
cd /pintos/src/threads
make clean
make
```

### Testing
```bash
cd build
perl /pintos/src/utils/pintos-mkdisk pintos_proper.img --kernel=kernel.bin
qemu-system-i386 -drive format=raw,file=pintos_proper.img -m 4 -nographic -monitor null
```

## Usage

1. **Start Pintos** - Boot with no command line arguments to trigger interactive shell
2. **Available Commands** - Type any of the seven supported commands
3. **Input Editing** - Use backspace to edit commands before pressing Enter
4. **Exit Options** - Use `exit` to return to kernel or `shutdown` to power off

## Achievements

- ✅ Kernel-level programming without standard C library
- ✅ Direct hardware interaction through Pintos APIs
- ✅ Memory management and thread system integration
- ✅ Real-time clock access for Unix timestamp
- ✅ Professional user interface design
- ✅ Robust input handling and error management

## Future Development

This README will be updated as additional features are implemented in subsequent weeks of the course. Planned enhancements may include:
- Advanced command parsing
- File system operations
- Process management commands
- Memory management utilities
- Network diagnostics

## Academic Integrity

This implementation represents original work completed for CS2042 coursework. The Pintos framework is used under its original license, with modifications limited to the interactive shell implementation as specified in the assignment requirements.

---

*Last Updated: August 2025*