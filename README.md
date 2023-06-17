# SR Flip Flop using NOR Gate

# THEORY
A Set-Reset (SR) flip-flop is a sequential logic circuit that can store one bit of information. It has two inputs, namely Set (S) and Reset (R), and two outputs, Q (the normal output) and Q_bar (the complement of Q). The SR flip-flop can be implemented using NOR gates.

The truth table for an SR flip-flop with inputs S and R is as follows:

![truth table](https://github.com/Sanjay-2610/Simulation-project--Digital-Electronics/assets/91368803/7c84e523-3d5d-412a-957c-2d00c47860b0)

The behavior of the SR flip-flop is determined by the inputs S and R. When S = 0 and R = 0, the flip-flop maintains its previous state. When S = 0 and R = 1, the flip-flop is reset, meaning Q = 0 and Q_bar = 1. When S = 1 and R = 0, the flip-flop is set, meaning Q = 1 and Q_bar = 0. When S = 1 and R = 1, the inputs are considered invalid (also known as a forbidden state) because it violates the expected behavior of a flip-flop.

The implementation of an SR flip-flop using NOR gates involves combining NOR gates to achieve the desired behavior. The NOR gate is chosen because it is a universal gate and can be used to construct other gates.

In the circuit, the NOR gates are interconnected to create a latch-like behavior. When S = 0 and R = 0, both inputs to the NOR gates are 1, causing the outputs to be 0 (Q = 0 and Q_bar = 0). When S = 0 and R = 1, the output of the lower NOR gate is 1, while the output of the upper NOR gate is determined by the current state of Q. This makes Q = 0 and Q_bar = 1. Similarly, when S = 1 and R = 0, Q = 1 and Q_bar = 0. The forbidden state of S = 1 and R = 1 is avoided due to the feedback from the outputs to the inputs of the NOR gates, ensuring stable operation.

The SR flip-flop has various applications in digital circuits, including memory elements, storage units, and control circuits. However, it has a potential drawback of entering the forbidden state if both S and R inputs change simultaneously. To avoid this issue, other types of flip-flops, such as the D flip-flop or JK flip-flop, are commonly used.

# LOGIC DIAGRAM
![Clocked-SR-flip-–-flop-using-NOR-gates](https://github.com/Sanjay-2610/Simulation-project--Digital-Electronics/assets/91368803/adec3d99-ea61-4099-9d92-eb50f2a65f61)


# NETLIST DIAGRAM
![rtl_Diagram](https://github.com/Sanjay-2610/Simulation-project--Digital-Electronics/assets/91368803/ec4d64f0-2e05-45b9-8c41-771ac29901b2)
# TIMING DIAGRAM
![Screenshot 2023-06-17 120807](https://github.com/Sanjay-2610/Simulation-project--Digital-Electronics/assets/91368803/87aa59e5-bb3d-429e-9ca3-a8457739b518)


# PROGRAM
```verilog
module lab(S,R,clk,Q,Qbar);
	input S,R,clk;
	output reg Q;
	output reg Qbar;
	initial Q=0;
	initial Qbar=1;
	always @(posedge clk)
	begin
	Q=S|((~R)&Q);
	Qbar=R|((~S)&(~Q));
	end
	endmodule
```
# REFERENCE
SR flip-flop using NOR gate | Digital Electronics (Gate Smashers) - Youtube

https://youtu.be/ZWikSnUxka8
