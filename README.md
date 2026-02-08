# ARITHMETIC-LOGIC-UNIT-ALU-

company:CODTECH IT SOLUTIONS

name: Gagguturu Pavan

intern ID::CTIS3423

DOMAIN:VLSI DESIGN

DURATION:4 MONTHS

MENTOR: Neela Santhosh Kumar

I WILL DO INTERNSHIP ON VLSI DESIGN IN VLSI DESIGN I WILL PERFORMED THE SECOND TASK IS RAM DESIGN THE RAM DESIGN CAN BE IMPLEMENTED ON EDA PLAYGROUND I WRITE VERILOG AND TESTBENCH IN EDA PLAYGROUND AFTER COMPLETION OF CODE I RUN THIS PROGRAM BY USING TOOLS LIKE IVERILOG AND EPWAVE IVERILOG IS USED TO RUN THE PROGRAMM AND EPWAVE IS USED FOR SIMULATION OF WAVEFORMS
ALU Design in Verilog
// ALU - Basic ALU Module
module alu(
    input [7:0] A, B,        
    input [2:0] op,          
    output reg [7:0] out,    
    output reg carry        
);

    always @(*) begin
        carry = 0;
        case(op)
            3'b000: {carry, out} = A + B;  
            3'b001: out = A - B;           
            3'b010: out = A & B;          
            3'b011: out = A | B;           
            3'b100: out = ~A;              
            default: out = 8'h00;
        endcase
    end
endmodule

Testbench for the ALU
// ALU - Testbench for ALU
