## NAME: ESWANTH KUMAR K
## REG NO: 212223040046
# SR-FLIPFLOP-USING-CASE

**AIM:**

To implement  SR flipflop using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

SR Flip-Flop SR flip-flop operates with only positive clock transitions or negative clock transitions. Whereas, SR latch operates with enable signal. The circuit diagram of SR flip-flop is shown in the following figure.

![image](https://github.com/naavaneetha/SR-FLIPFLOP-USING-CASE/assets/154305477/0f710028-ad52-4d3e-9276-8714cf023a25)

 
This circuit has two inputs S & R and two outputs Qtt & Qtt’. The operation of SR flipflop is similar to SR Latch. But, this flip-flop affects the outputs only when positive transition of the clock signal is applied instead of active enable. The following table shows the state table of SR flip-flop.

![image](https://github.com/naavaneetha/SR-FLIPFLOP-USING-CASE/assets/154305477/dabfc4f4-87e3-4cbc-9472-f89ee1b5ed30)

 
Here, Qtt & Qt+1t+1 are present state & next state respectively. So, SR flip-flop can be used for one of these three functions such as Hold, Reset & Set based on the input conditions, when positive transition of clock signal is applied. The following table shows the characteristic table of SR flip-flop. Present Inputs Present State Next State

![image](https://github.com/naavaneetha/SR-FLIPFLOP-USING-CASE/assets/154305477/dd90d16c-aec5-4290-a586-e2346b1e9eb5)

 
By using three variable K-Map, we can get the simplified expression for next state, Qt+1t+1. The three variable K-Map for next state, Qt+1t+1 is shown in the following figure.

![image](https://github.com/naavaneetha/SR-FLIPFLOP-USING-CASE/assets/154305477/473efad6-d70b-4ca7-aeb7-898bbfca319f)

 
The maximum possible groupings of adjacent ones are already shown in the figure. Therefore, the simplified expression for next state Qt+1t+1 is Q(t+1)=S+R′Q(t)Q(t+1)=S+R′Q(t)

**Procedure**

1. Inputs and Outputs: 
   The module sr_flipflop has inputs s, r, clk, and reset, and outputs q and q_bar.
   
2. Clocked Process:
   The always @(posedge clk) block defines a clocked process sensitive to the positive edge of the clock signal.
   
3. Reset Handling:
   If the reset signal is asserted (logic low), the flip-flop resets. In this case, the output q is forced to 0.
   
4. State Transition:
   If the reset signal is de-asserted (logic high), the flip-flop behaves according to the inputs s (set) and r (reset). It uses a case statement to determine the behavior 
   based on the combination of s and r:
   
   If s=0 and r=1 (set condition), the output q is set to 0.
   
   If s=1 and r=0 (reset condition), the output q is set to 1.
   
   If s=1 and r=1 (invalid condition), the output q enters an indeterminate state (x).
   
   For all other combinations of s and r, the output q remains unchanged.
   
6. Output Complementation:
   The output q_bar is complemented (~q), i.e., the logical negation of q.




**PROGRAM**

Program for flipflops and verify its truth table in quartus using Verilog programming.

Developed by: ESWANTH KUMAR K

RegisterNumber: 212223040046


```
module sr_flipflop(q, q_bar, s, r, clk, reset);
  input s, r, clk, reset;
  output reg q;
  output q_bar;

  always @(posedge clk) begin
    if (!reset) 
      q <= 1'b0;
    else begin
      case ({s, r})
        2'b01: q <= 1'b0;
        2'b10: q <= 1'b1;
        2'b11: q <= 1'bx;
        default: q <= q;
      endcase
    end
  end

  assign q_bar = ~q;
endmodule

```


**RTL LOGIC FOR FLIPFLOPS**
<img width="960" alt="RTL sr_flipflop" src="https://github.com/Ganesh23013987/SR-FLIPFLOP-USING-CASE/assets/147473768/52c07e28-f65a-43d4-8531-73b70b27296e">


**TIMING DIGRAMS FOR FLIP FLOPS**
<img width="960" alt="sr_flipflop" src="https://github.com/Ganesh23013987/SR-FLIPFLOP-USING-CASE/assets/147473768/784f26d6-71de-46fb-95bc-9661a1382518">



**RESULT**

Thus the program to implement a SR flipflop using verilog and validating their functionality using their functional tables is successfully completed.
