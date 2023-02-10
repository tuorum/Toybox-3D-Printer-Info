# Toybox-3D-Printer-Info
This repo has several files of settings or informations for the Toybox 3d Printer.

Toybox print settings - from g-code log.txt - The first few lines are interpolated from the gcode extracted from the microSD card in the unit,
      which contains a raw text partition caching gcode that is sent to the printer.  The lines beginning with a semi-colon are comments from the same log
      for a different print.  Based on the terminology alone, it looks like PrusaSlicer or Slic3r output.  These were probably other models from the
      Toybox website.

Toybox-gcode-list-2.txt - a list of the active gcode in the Toybox firmware.

toybox.km - Kiri:moto (browser-based slicer here: https://grid.space/kiri/).  Load via the "Files" icon on the left, the same as you load STLs.

The Toybox gcode appears to be mostly based of Repetier.  Some settings can be modified via the Repetier EEPROM gcodes to attempt to adjust things such as e-steps
      and linear advance.


USB/Serial access:
      Need to use 250000 baud.  And to send gcode you need to type it pretty quick, or the input loop will quit out and just start looking an "Resend: ok" prompt.
      It will still take input, just have to do it quickly.  There is no echo to the terminal.  There is no G503, so see the gcode list here.

Board info:
      Firmware seems to show it being ROBIN, but the layout is not a normal robin board.
      STM32F103 VET6 32-bit ARM CPU, HB4988 stepper drivers, 24V input current.
      There is a second board attached via a 4-pin connection.  This board is a ESP12 wifi microcontroller, which has the guts for communicating with the toybox site.
      ROM contents currently unknown.  With the secondary board detached, the system will not boot and sticks at the "Booting" splash screen.  This indicates the
      firmware is customized ROBIN to look for the secondary wifi board to continue booting.  Have not yet connected a serial interface to it to see what is being
      transmitted.

Note: This was gained from a "ALPHA" model Toybox with the GD32F303VET6 processor.  The model for sale currently appears to be STM32F303VET6 based.
