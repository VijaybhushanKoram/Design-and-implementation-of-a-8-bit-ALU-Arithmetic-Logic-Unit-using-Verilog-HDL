# Design-and-implementation-of-a-8-bit-ALU-Arithmetic-Logic-Unit-using-Verilog-HDL
In this project, we will design and implement a 8-bit ALU using Verilog HDL. The ALU will perform basic arithmetic and logic operations such as addition, subtraction, AND, OR, XOR, and complement. We will implement the ALU using combinational logic, which means that it will not have any internal state.
/// Code for design you can replace other operations if u want !!!!

module alu(
  
  input [7:0]A,
  input [7:0]B,
  input [2:0]op,
  
//output
  
  output reg [7:0]out
);
  
  always@(*)
   begin
     case(op)
       3'b000:out=(A+B);
       3'b001:out=(A-B);
       3'b010:out=(A^B);
       3'b011:out=(A&B);
       3'b100:out=(A|B);
       3'b101:out=(~A);
       3'b110:out=(~B);
       3'b111:out=4'b0000;
       default:out=4'b0000;
     endcase
   end
  
endmodule

Here am certainly including some test cases for the code

 module alu_tb();
  
  reg[7:0]A;
  reg[7:0]B;
  reg[2:0]op;

  
  //output
  
  wire[7:0]out;
  
  
  alu dut(
    .A(A),
    .B(B),
    .op(op),
    .out(out)
  );
  
  
 
  reg clk=1'b0;
  always #5 clk=~clk;
  
  
  initial begin
    //test case 1
    
    A=8'b00000101;
    B=8'b00000011;
    op=3'b000;
    $display(" output = %b expected output 00001000",out);
  
    #10;
    
       
    A=8'b00000101;
    B=8'b00000011;
    op=3'b001;

    
    #10;
    $display(" output = %b expected output 00000010",out);    
    
       
    A=8'b00000101;
    B=8'b00000011;
    op=3'b010;

    
    #10;
    
    $display(" output = %b expected output 00000001",out); 
    
       
    A=8'b00000101;
    B=8'b00000011;
    op=3'b011;
 
    
    #10;
    $display(" output = %b expected output 00000110",out);
    
    $finish;
    
  end
  
endmodule


