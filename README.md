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
// 4-Bit ALU Design Module
module ALU_4bit (
    input  [3:0] A_in,      // 4-bit Input A
    input  [3:0] B_in,      // 4-bit Input B
    input  [2:0] Op_code,   // 3-bit Operation Select
    output reg [3:0] ALU_result,
    output reg C_out,       // Carry Out Flag
    output Z_flag           // Zero Flag
);

    always @(*) begin
        // Initialize Carry to 0 to avoid latches
        C_out = 1'b0;
        
        case (Op_code)
            3'b000: {C_out, ALU_result} = A_in + B_in; // Addition
            3'b001: {C_out, ALU_result} = A_in - B_in; // Subtraction
            3'b010: ALU_result = A_in & B_in;          // Logical AND
            3'b011: ALU_result = A_in | B_in;          // Logical OR
            3'b100: ALU_result = ~A_in;               // Logical NOT
            default: ALU_result = 4'b0000;             // Default/Reset
        endcase
    end

    // Zero Flag logic: High if ALU_result is 0
    assign Z_flag = (ALU_result == 4'b0000);

endmodule

Testbench for the ALU
// ALU - Testbench for ALU
// Testbench for 4-Bit ALU
module ALU_tb;

    // Internal signals
    reg [3:0] A_in, B_in;
    reg [2:0] Op_code;
    wire [3:0] ALU_result;
    wire C_out, Z_flag;

    // Instantiate the Unit Under Test (UUT)
    ALU_4bit uut (
        .A_in(A_in),
        .B_in(B_in),
        .Op_code(Op_code),
        .ALU_result(ALU_result),
        .C_out(C_out),
        .Z_flag(Z_flag)
    );

    initial begin
        // Generate VCD file for waveform analysis
        $dumpfile("alu_waves.vcd");
        $dumpvars(0, ALU_tb);

        // Display results in the console
        $display("Time | Op | A | B | Result | C | Z");
        $monitor("%4t | %b | %h | %h |   %h    | %b | %b", 
                 $time, Op_code, A_in, B_in, ALU_result, C_out, Z_flag);

        // --- Test Cases ---
        
        // Test 1: Addition (5 + 3 = 8)
        A_in = 4'h5; B_in = 4'h3; Op_code = 3'b000; #10;
        
        // Test 2: Subtraction (5 - 3 = 2)
        A_in = 4'h5; B_in = 4'h3; Op_code = 3'b001; #10;
        
        // Test 3: Bitwise AND
        A_in = 4'hC; B_in = 4'hA; Op_code = 3'b010; #10;
        
        // Test 4: Bitwise OR
        A_in = 4'hC; B_in = 4'hA; Op_code = 3'b011; #10;
        
        // Test 5: Bitwise NOT
        A_in = 4'hA; B_in = 4'h0; Op_code = 3'b100; #10;
        
        // Test 6: Zero Flag Verification
        A_in = 4'h0; B_in = 4'h0; Op_code = 3'b000; #10;

        $finish;
    end

endmodule
