Aim
To design and simulate a seven-segment display driver using Verilog HDL, and verify its functionality through a testbench in the Vivado 2023.1 environment. The objective is to implement the logic that converts a 4-bit binary input into the corresponding 7-segment display output for the digits 0 to 9.

Apparatus Required
Vivado 2023.1
Computer system with a suitable operating system.

Procedure

Launch Vivado 2023.1:

Open Vivado and create a new project.
Design the Verilog Code:

Write the Verilog code for the seven-segment display, defining the logic that maps a 4-bit binary input to the corresponding segments (a to g) of the display.
Create the Testbench:

Write a testbench to simulate the seven-segment display behavior. The testbench should apply various 4-bit input values and monitor the corresponding output on the seven-segment display.
Add the Verilog Files:

Add both the design module and the testbench in the Vivado project.
Run Simulation:

Run the behavioral simulation to verify the output. Ensure the seven-segment display behaves correctly for binary inputs 0000 to 1001 (decimal 0 to 9).
Observe the Waveforms:

Analyze the output waveforms in the simulation window, and verify that the correct segments light up for each digit.
Save and Document Results:

Capture screenshots of the waveform and save the simulation logs. These will be included in the lab report.

Diagram
![image](https://github.com/user-attachments/assets/d7ecb419-906e-4e3b-9b82-f86ced4f364a)


Verilog Code for Seven-Segment Display

module bcd(bcd,seg);
input[3:0]bcd;
output reg [7:0]seg;
always@(*)
case(bcd)
  0:seg=7'b0000001;
  1:seg=7'b1001111;
  2:seg=7'b0010010;
  3:seg=7'b0000110;
  4:seg=7'b1001100;
  5:seg=7'b0100100;
  6:seg=7'b0100000;
  7:seg=7'b0001111;
  8:seg=7'b0000000;
  9:seg=7'b0000100;
default:seg=7'b1111111;
endcase
endmodule
![Screenshot (9)](https://github.com/user-attachments/assets/43bd3be7-0f79-4128-ba9c-e124c9ac8ec6)



Testbench for Seven-Segment Display:

module bcd_tb; // Inputs 
reg [3:0] bcd;

// Outputs
wire [6:0] seg;

// Instantiate the Unit Under Test (UUT)
bcd uut (
    .bcd(bcd),
    .seg(seg)
);

// Test procedure
initial begin
    // Initialize inputs
    bcd = 4'b0000;

    #10 bcd = 4'b0000; // Display 0
    #10 bcd = 4'b0001; // Display 1
    #10 bcd = 4'b0010; // Display 2
    #10 bcd = 4'b0011; // Display 3
    #10 bcd = 4'b0100; // Display 4
    #10 bcd = 4'b0101; // Display 5
    #10 bcd = 4'b0110; // Display 6
    #10 bcd = 4'b0111; // Display 7
    #10 bcd = 4'b1000; // Display 8
    #10 bcd = 4'b1001; // Display 9
    #10 $stop;
end

// Monitor outputs

endmodule
![Screenshot (12)](https://github.com/user-attachments/assets/379de5d5-d59b-46ee-abd9-5079a4764299)

Conclusion
In this experiment, a seven-segment display driver was successfully designed and simulated using Verilog HDL. The simulation results confirmed that the display correctly represented the digits 0 to 9 based on the 4-bit binary input. The testbench effectively verified the functionality of the seven-segment display by applying various input combinations and observing the corresponding segment outputs. This experiment highlights how Verilog HDL can be used to control hardware components like a seven-segment display in digital systems.
