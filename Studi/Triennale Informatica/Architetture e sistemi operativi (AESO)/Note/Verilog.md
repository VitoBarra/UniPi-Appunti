---
Course: Architettura E Sistemi Operativi
topic: nota
tags: AESO
---

Prev: [[Architetture e sistemi operativi (AESO)]]

# Verilog
---


```verilog

reg/wire [31:0]pippo[256];
integer n;
4'b0111

moduli
astrazione di un componente (combinatorio o sequenziale)

module M(output z, output reg r, input x, input y);
    parameter N = 32;
    parameter M = 8;

    ...
endmodule

M m0(d, n, m);
M #(16, 2) m1(d, n, m);

testbench
moduli senza parametri -- per testare componenti

```verilog
module test();
    ...
    #42 $finish;
endmodule

```

initial/always begin ... end

reg clock;
initial clock = 0
always #1 clock = ~clock

always @([negedge/posedge] x, y) / @(*)

assegnamento
=            : bloccante
<=           : non bloccante
assign x = y : continuo
=/<= solo su registro, assign anche su wire

#1 x = y;    : aspetta 1 e poi assegna y a x
x = #1 y;    : calcola y, aspetta 1 e poi assegna

swap: x <= y; y <= x

for/while (...) begin ... end
for sintetizzabile
includere in un componente un numero variabile di altri componenti
    genvar i;
    generate
        for (i = 0; i < N; i = i + 1) begin ... end
    endgenerate

corpo while deve avere temporizzazione
case (e)
v1: begin ... end
...
default: begin ... end
endcase

$monitor("%t %d", $time, clock);
$dumpfile("clock.vcd"); $dumpvars;

```

reti combinatorie

- tabella di verità (un solo output)
primitive rc(output z, input x, input y);
table
0 0 : 0 ;
0 1 : 1 ;
1 ? : 0 ;
endtable
endprimitive
- espressioni booleane
module m(output z, output w, input x, input y);
assign z = x & y;
assign w = x | y;
endmodule

    module somma(output [N-1:0]z, output cout, input [N-1:0]x, input [N-1:0]y, input cin)
    assign {cout, z} = x + y + cin;
    endmodule

    modellare ritardi (2 livelli):
    assign #2 z = (x & y) | (~x & z);


reti sequenziale

- modello strutturale
due reti combinatorie (primitive/module) e un registro


    ```verilog

    module seq(output out, input in, input clk);
    	wire regin;
    	wire regout;
      registro stato(regout, regin, clk);
      combstato s(regin, regout, in);
      combuscita u(out, in, regout);
    endmodule

    ```

- modello behavioural
programmare la rete invece di combinari altri moduli
stato mantenuto con reg


    ```verilog
    module seq(...);
    reg [...]stato;
    	initial stato <= ...;
      always @(posedge clock) stato <= prossimostato;
      always @(ingresso, stato) prossimostato <= exp;
      assign uscita = ...
    endmodule
    ```

    serve <= per fare gli assegnamenti in parallelo tra i blocchi altrimenti non corretto
