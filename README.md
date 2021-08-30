# Traffic Light Controller Using Verilog
* The purpose of this project is to design a methodology using Verilog to control the traffic with specified time delays for a T-Shaped road.*

# Table of Contents

1. [Introduction](#Introduction)
2. [Methodology](#Methodology)
    - [Directions Considered](#directions-considered)
    - [Problem Statement](#problem-statement)
    - [State Diagram](#state-diagram)
    - [State Table](#state-table)
3. [RTL Code](#rtl-code)
    - [RTL Schematic View](#rtl-schematic-view)
4. [TESTBENCH](#testbench)
5. [Output Waveforms](#output-waveforms)
6. [Result](#result)
7. [Future work](#future-work)
8. [References](#references)
9. [Author](#author)


## Introduction 

Traffic control is a challenging problem in many cities. This is due to the large number of vehicles and the high dynamics of the traffic system. Poor traffic systems are the big reason for accidents, time losses. In this method of approach, it will reduce the waiting time of the vehicles at traffic signals. The hardware design has been developed using Verilog Hardware Description Language (HDL) programming. 

Verilog designing is hardware descriptive language, the name itself suggest that it deals with the hardware designing and simulation. Basically, it becomes very difficult to mount the various electronic components on breadboard or PCB circuit. It also takes too much time for the simulation and sometimes many errors occur because of improper connection of components onto the circuit. 
And thus, to overcome this factor hardware descriptive language comes into conclusion. we can code the process using Verilog and we can mount it on a circuit or just upload it to the circuit accordingly so that particular circuit will work as according to the code we have written. 

HDL language is often used for sequential circuits like shift register, combinational logic circuit like adder, subtractor etc. Basically it describes the digital systems like microprocessor or a memory. Whatever design that is described in HDL are independent, it has its unique state of work, very much easy to simulate, designing and debugging, and very useful than schematics, especially for large circuits thus, to overcome difficulties or problems to design the circuits manually with breadboard and PCB, use of Verilog designing in this complex world is increasing a way better. 

This project deals with a basic design of a T - Shaped road for traffic light control. The output of system has been tested using Xilinx 14.5. 

A traffic light system is an electronic device that assigns right of way at an intersection or crossing or street crossing by means of displaying the standard red, yellow and green colored indications. In addition, it also works in conjunction with pedestrian displays to assign pedestrian crossing right of way. 

A traffic light, also known as traffic signal, stop light, stop-and-go lights, is a signaling device positioned at a road intersection, pedestrian crossing, or other location in order to indicate when it is safe to drive, ride, or walk using a universal colour code.
Nowadays, 

1. A red light meant traffic in all directions had to stop. 
2. A yellow light meant cross-town traffic would have to slow and,
3. A green light would to go or proceed.

The problem of heavy jam is happened because of never configure the level of jam in each way and set the delay time. Another problem represents when there is no jam, but the waiting still continues. The solution for these problems is to determine the level of jam and set the delay time. This problem need of evaluation of the traffic policeman, and then there is need for manual control of the traffic. 
The target of this paper is to propose system provide solution for all above problems with least possible cost. Traffic light controller (TLC) can be implemented using microcontroller, FPGA, and ASIC design. FPGA has many advantages over microcontroller, some of these advantages are; the speed, number of input/output ports and performance which are all very important in TLC design, at the same time ASIC design is more expensive than FPGA. 
Nowadays, FPGA becomes one of the most successful of today’s technologies for developing the systems which require a real time operation. FPGA is a re-configurable integrated circuit that consists of two dimensional arrays of logic blocks and flip-flops with an electrically programmable interconnection between logic blocks. 
The reconfiguration property enables fast prototyping and updates for hardware devices even after market launch. Most of the TLCs implemented on FPGA are simple ones that have been implemented as examples of Finite State Machine (FSM).

#### The Verilog language has been selected for programming the FPGA to fill two important needs in the design process. 

- Firstly, it gives full description of the structure of a design that is how it is decomposed into sub-designs, and how those sub-designs are interconnected. 
- Secondly, it allows simulating the design before starting the manufacturing. 
- Accordingly, the designers can quickly compare alternatives and test for correctness without the delay and expense of hardware prototyping. 

#### Benefits of Using Verilog HDL (Hardware Description Language) : 

Verilog is a widely used Hardware Description Language (HDL) for designing digital circuits. It can also be used for modeling analog circuits. Verilog is a descriptive language that describes a relationship between signals in a circuit. 

A Verilog model describes a unit of digital hardware in terms of :
- Interconnections of other hardware unit whose models prescribe their behavior in a 
    simulation.
- Behavioral / procedural algorithms that abstractly describe input/output behavior    
       that could be personified in a hardware unit. 

Hardware description language (HDL) is divided by two types, Verilog and VHDL (VHSIC – Very High Speed Integrated Circuit Hardware Description Language). Both have its advantages and its disadvantage. 
In this project, Verilog HDL was chosen because it’s used for synthesis of logic circuits (synthesizable code), used for verification purposes of a circuit (can be analog or digital or mixed signal), can be used by combining synthesis & verification (synthesizable & behavioral code) and it used for netlist representation of a synthesizable circuit (structural code). 

#### The advantages using Verilog HDL are shown below : 
- Easy to write. 
- Easy to understand as it similar to C program. 
- Easier to learn compared with VHDL.


## Methodology

### Directions Considered

![directions](https://user-images.githubusercontent.com/83152452/131366734-67c76e3c-b53d-49ca-a5ba-fb058d19d578.png)

The directions, M1, MT, M2, S, that is been considered for analysis of our problem is shown in the figure. And, the problem statement is explained in the figure. 
Six states, S1, S2, S3, S4, S5, S6 are taken into consideration and state diagram, state table is made using the following logic explained in the figure. 

### Problem Statement

![Logic_Diagram](https://user-images.githubusercontent.com/83152452/131366783-8c025386-8011-4ef9-a766-d0a07e4244ac.png)

- Green light indicates that there is no traffic and there is easy flow of vehicles in that route/direction. 
- Red light indicates that there is a traffic jam and that route is blocked for the vehicles to move and, 
- Yellow light indicates that the route has medium flow of vehicles. 

Time delays for changing from one state to another is considered as, TMG(from S1 to S2), TY(from S2 to S3), TTG(from S3 to S4), TY(from S4 to S5), TSG(from S5 to S6) 
and TY(from S6 to S1) and the cycle continues.


### State Diagram

![State_Diagram](https://user-images.githubusercontent.com/83152452/131366795-bc45473d-4398-47bb-bad9-a520a779c8bc.png)

In Figure, The time delays are considered as follows :

- TMG = 7 seconds
- TY = 2 seconds
- TTG = 5 seconds
- TSG = 3 seconds

Until TMG seconds, the signal will remain in S1 state, and after TMG seconds, it will move to S2 state. Until TY seconds it will remain in S2 state and after TY seconds, 
it will move to S3 state, and so on. After TY seconds, in state S6, it will go back to S1 state and the cycle continues.


### State Table

![StateTable](https://user-images.githubusercontent.com/83152452/131366804-309b6e9a-4c9c-442b-8753-281a933254f6.png)

In Figure, 
- R = RED, 
- Y = YELLOW and, 
- G = GREEN.

ST = State Transition; A, B and C are considered as the present state.
The state table is made, considering the Logic diagram/problem statement given in Figure. 
From the Figure it is understood that, 

In state S1(001);	

```
     1. M1 = GREEN, implies, RYG value = 001,
     2. MT = RED, implies, RYG value = 100,
     3. M2 = GREEN, implies, RYG value = 001 and,
     4. S = RED, implies, RYG value = 100.
     
```     
                 
After TMG seconds,

In state S2(010);	

```
      1. M1 = GREEN, implies, RYG value = 001, 
      2. MT = RED, implies, RYG value = 100,     
      3. M2 = YELLOW, implies, RYG value = 010 and,
      4. S = RED, implies, RYG value = 100.
      
```

After TY seconds,

In state S3(011);	

```
      1. M1 = GREEN, implies, RYG value = 001,
      2. MT = GREEN, implies, RYG value = 001,
      3. M2 = RED, implies, RYG value = 100 and,
      4. S = RED, implies, RYG value = 100.
      
```      
      
After TTG seconds,

In state S4(100);	

```
      1. M1 = YELLOW, implies, RYG value = 010,
      2. MT = YELLOW, implies, RYG value = 010,
      3. M2 = RED, implies, RYG value = 100 and,
      4. S = RED, implies, RYG value = 100.
      
```

After TY seconds,

In state S5(101);	

```
      1. M1 = RED, implies, RYG value = 100,
      2. MT = RED, implies, RYG value = 100,
      3. M2 = RED, implies, RYG value = 100 and,
      4. S = GREEN, implies, RYG value = 001.
      
```

After TSG seconds,

In state S6(110);

```
       1. M1 = RED, implies, RYG value = 100,
       2. MT = RED, implies, RYG value = 100,
       3. M2 = RED, implies, RYG value = 100 and,
       4. S = YELLOW, implies, RYG value = 010.

```

And after S6 state, the cycle repeats and goes to S1 state.




## RTL Code

```

`timescale 1ns / 1ps
module Traffic_Light_Controller(
    input clk,rst,
    output reg [2:0]light_M1,
    output reg [2:0]light_S,
    output reg [2:0]light_MT,
    output reg [2:0]light_M2 
	 );
	 
    parameter  S1=0, S2=1, S3 =2, S4=3, S5=4,S6=5;
    reg [3:0]count;
    reg[2:0] ps;
    parameter  sec7=7,sec5=5,sec2=2,sec3=3;
	 
    always@(posedge clk or posedge rst)
        begin
        if(rst==1)
        begin
        ps<=S1;
        count<=0;
        end
        else 
            case(ps)
                S1: if(count<sec7)
                        begin
                        ps<=S1;
                        count<=count+1;
                        end
                    else
                        begin
                        ps<=S2;
                        count<=0;
                        end
                S2: if(count<sec2)
                        begin
                        ps<=S2;
                        count<=count+1;
                        end
                    else
                        begin
                        ps<=S3;
                        count<=0;
                        end
              S3: if(count<sec5)
                        begin
                        ps<=S3;
                        count<=count+1;
                        end
                    else
                        begin
                        ps<=S4;
                        count<=0;
                        end
                S4:if(count<sec2)
                        begin
                        ps<=S4;
                        count<=count+1;
                        end
                    else
                        begin
                        ps<=S5;
                        count<=0;
                        end
                S5:if(count<sec3)
                        begin
                        ps<=S5;
                        count<=count+1;
                        end
                    else
                        begin
                        ps<=S6;
                        count<=0;
                        end
                S6:if(count<sec2)
                        begin
                        ps<=S6;
                        count<=count+1;
                        end
                    else
                        begin
                        ps<=S1;
                        count<=0;
                        end
                default: ps<=S1;
                endcase
            end   

            always@(ps)    
            begin   
           case(ps)          
                    S1:
                    begin
                       light_M1<=3'b001;
                       light_M2<=3'b001;
                       light_MT<=3'b100;
                       light_S<=3'b100;
                    end
                    S2:
                    begin 
                       light_M1<=3'b001;
                       light_M2<=3'b010;
                       light_MT<=3'b100;
                       light_S<=3'b100;
                    end
                    S3:
                    begin
                       light_M1<=3'b001;
                       light_M2<=3'b100;
                       light_MT<=3'b001;
                       light_S<=3'b100;
                    end
                    S4:
                    begin
                       light_M1<=3'b010;
                       light_M2<=3'b100;
                       light_MT<=3'b010;
                       light_S<=3'b100;
                    end
                    S5:
                    begin
                       light_M1<=3'b100;
                       light_M2<=3'b100;
                       light_MT<=3'b100;
                       light_S<=3'b001;
                    end
                    S6:
                    begin 
                       light_M1<=3'b100;
                       light_M2<=3'b100;
                       light_MT<=3'b100;
                       light_S<=3'b010;
                    end
  default:
                    begin 
                       light_M1<=3'b000;
                       light_M2<=3'b000;
                       light_MT<=3'b000;
                       light_S<=3'b000;
                    end
                  endcase
            end                         
endmodule


```

### RTL Schematic View

![RTL Schematic View](https://user-images.githubusercontent.com/83152452/131369733-eb1964e5-319f-4997-9b3e-6f6ee3e2fb6e.jpeg)


## TESTBENCH

```

`timescale 1ns / 1ps
module Traffic_Light_Controller_TB;
reg clk,rst;
wire [2:0]light_M1;
wire [2:0]light_S;
wire [2:0]light_MT;
wire [2:0]light_M2;
wire [3:0] count;
wire [2:0]ps;
Traffic_Light_Controller dut(.clk(clk) , .rst(rst) , .light_M1(light_M1) , .light_S(light_S)  ,.light_M2(light_M2),.light_MT(light_MT)  );
initial
begin
    clk=1'b0;
    forever #(1000000000/2) clk=~clk;
end

initial
begin
    rst=0;
    #1000000000;
    rst=1;
    #1000000000;
    rst=0;
    #(1000000000*200);
    $finish;
end
endmodule

```


## Output Waveforms


![Output_waveform-1](https://user-images.githubusercontent.com/83152452/131370429-58f902d3-c104-45b5-95d6-1ca116aad0b2.jpeg)

![Output_waveform-2](https://user-images.githubusercontent.com/83152452/131370436-da8ce8c4-5afe-4567-b893-7d99ae9cd23e.jpeg)

![Output_waveform-3](https://user-images.githubusercontent.com/83152452/131370443-ac740d0d-8fa6-49ef-b478-af36d457b6f3.jpeg)


## Result

In this model we have observed various stages which describes about every signals. For example, Consider that at first stage (north-south end) signals gives some indication. 
Then, the signal is red that means signal at east-west side gives a green indication and traffic moves to their respective direction. Then after some delay yellow signal is 
obtain at east-west side and after the red signal arrives at the same time at the north-south end red signal goes off and green signal gets on and traffic moves to their 
particular direction. In this way process continues in the loop every day. 

The modern ways of multi-way traffic management improves the traffic condition up to a large extent. Traffic intensity is sensed and accordingly time is allotted for traffic to
pass. Verilog HDL is used to circuit description, code is generated which is simulated using Xilinx14.5.

This traffic light control system works on the concept of fixed time allocation at each side of the junction which cannot be changed as per varying traffic density. 
Timings allotted at every junction are fixed. Sometimes higher traffic density at one side of the junction demands longer time duration for green signal compared to the 
standard allotted time.

Thus, traffic light control system helps to conduct orderly flow of vehicles. There are lot many issues of obstacles, high level accidents which occurs every day. 
So, traffic signal controller prevents such occurrences. Still many areas or small towns don’t have the traffic light control facilities. And thus, many accident problems occur 
at those areas. Therefore, it is a primary purpose to have such facility in order to control and maintain the area.


## Future Work

This project can be enhanced in such away as to control automatically the signals depending on the traffic density on the roads using sensors like IR detector/receiver module 
extended with automatic turn off when no vehicles are running on any side of the road which helps in power consumption saving. 

A lot of development ideas for work in future can be implemented, such as using solar energy (independent power supply, i.e. saving the power). Using the GPRS map as an 
additional step for development and choosing the best road for the emergency and police vehicles. For national highways we can also design the 8 road traffic light controllers.


## References

1) Laboratory Exercise #12, The Traffic Light Controller Lab. “ECEN 248: Introduction to Digital Design”. Department of Electrical and Computer Engineering Texas A&M University.

2) Rajeev Madhavan, Verilog HDL Reference Guide, Automata Publishing Company, CA, 1993. ISBN 0-9627488-4-6

3) E. Sternheim, Rajvir Singh, Rajeev Madhavan, Yatin Trivedi, Digital Design and Synthesis with Verilog HDL, Automata Publishing Company, CA, 1993. ISBN 0-9627488-2-X

4) https://intentswell.blogspot.com/2021/03/traffic-light-controller-project-report.html

5) https://www.semanticscholar.org/paper/An-Advanced-Traffic-Light-Controller-using-Verilog-B.-ala/1ca8a8e50c2c8273a3ee1247a6057f8eb4f402ee

6) https://www.academia.edu/21200096/DESIGN_AND_IMPLEMENTATION_OF_TRAFFIC_LIGHTS_CONTROLLER_USING_FPGA_A_Project_Based_Laboratory_Report_in_partial_fulfilment_for_the_award_of_III_IV_B_Tech_I_Semester_Submitted_by_Lab_Instructor

7) https://vlsicoding.blogspot.com/2013/11/verilog-code-for-traffic-light-control.html 

8) https://www.fpga4student.com/2016/11/verilog-code-for-traffic-light-system.html 

9) https://www.slideshare.net/UtkarshDe/four-way-traffic-light-conrol-using-verilog 


## Author

- [A Devipriya](https://github.com/Devipriya1921), Bachelor of Engineering in Electronics and Communication Engineering, Cambridge Institute of Technology, Bangalore

    
