This project is to better control the UVvis machine with tensile tester, polarizer, and keithley.

There will be subfolder:

- `firmware`: arduino code to control the laod frame, receive encoder values, and actuarte polarizer
  - `main` setup and loop, includes interfaces for other components. All serial communications are done here. error checking, maintains state, handles general commands
  - `polarizer` Controls the polarizer servo, which can toggle ||, \perp, and unpolarized states via rotration
  - `stepper` Receives step counts, performs steps
  - `encoder` Returns encoder counts for validation
- `arduino_control` - send steps, polarizer, and receive encoder counts
  - `polarizer` - control polarizer orientation by implement serial commands compatoble with firmware
- `shimadzu` python module to control uv-vis machine using the serial protocol.
  - `spectra` control spectra measurements, receive data
  - `photometric` sets a wavelength and read data
- `keithley` uses serial to control a keitlhy 2450 source meter. 
  - `sweep` performs sweep
  - `basic_smu` allows reading a writing of scalar values
- `app` pyQT gui that runs on host computer, uses `shimadzu`,`keitlhey`,and `arduino_control`
  - `...`