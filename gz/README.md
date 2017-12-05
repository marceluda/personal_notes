# Guardo info sobre cómo usar GraphViz


Esto es muy útil para documentar diagramas de flujo


**Links útiles**
- http://graphs.grevian.org/example
- http://www.graphviz.org/doc/info/attrs.html
- http://graphviz.readthedocs.io
- https://stackoverflow.com/questions/7922960/block-diagram-layout-with-dot-graphviz

## Ejemplo de código

```js
digraph G {
    graph [rankdir = LR];

    node[shape=record];
    Bar[label="{ \"Bar\"|{<p1>pin 1|<p2>     2|<p3>     3|<p4>     4|<p5>     5} }"];
    Foo[label="{ {<data0>data0|<data1>data1|<data2>data2|<data3>data3|<data4>data4}|\"Foo\" |{<out0>out0|<out1>out1|<out2>out2|<GND>gnd|<ex0>ex0|<hi>hi|<lo>lo} }"];

    Bew[label="{ {<clk>clk|<syn>syn|<mux0>mux0|<mux1>mux1|<signal>signal}|\"Bew\" |{<out0>out0|<out1>out1|<out2>out2} }"];
    Bar:p1 -> Foo:data0;
    Bar:p2 -> Foo:data1;
    Bar:p3 -> Foo:data2;
    Bar:p4 -> Foo:data3;
    Bar:p5 -> Foo:data4;

    Foo:out0 -> Bew:mux0;
    Foo:out1 -> Bew:mux1;
    Bew:clk -> Foo:ex0;

    Gate[label="{ {<a>a|<b>b}|OR|{<ab>a\|b} }"];

    Foo:hi -> Gate:a;
    Foo:lo -> Gate:b;
    Gate:ab -> Bew:signal;
}
```

## Para usar desde python

Necesitas instalarlo en anaconda:

```bash
./conda install graphviz
./conda install python-graphviz
```

Luego podes incluirlo:


```python
from graphviz import Digraph
dot = Digraph(comment='verilog1')

#%%
dot.node('A', 'King Arthur')

dot.node('B', 'Sir Bedevere the Wise')
dot.node('L', 'Sir Lancelot the Brave')

dot.edges(['AB', 'AL'])
dot.edge('B', 'L', constraint='false')

print(dot.source)

#%%
dot.format='svg'
dot.view()

#%%
dot.format='pdf'
dot.view()
```

fuente: http://graphviz.readthedocs.io/en/stable/examples.html



Mas ejemplos:

```python

dot = Digraph(comment='verilog1')

dot.graph_attr['rankdir'] = 'LR'
dot.node_attr['shape']='record'

dot.node('Bar', "{ Bar|{<p1>pin 1|<p2>     2|<p3>     3|<p4>     4|<p5>     5} }")
dot.node('Foo', "{ {<data0>data0|<data1>data1|<data2>data2|<data3>data3|<data4>data4}|Foo |{<out0>out0|<out1>out1|<out2>out2|<GND>gnd|<ex0>ex0|<hi>hi|<lo>lo} }" )
dot.node('Bew', "{ {<clk>clk|<syn>syn|<mux0>mux0|<mux1>mux1|<signal>signal}|Bew |{<out0>out0|<out1>out1|<out2>out2} }" )

dot.edge('Bar:p1', 'Foo:data0')
dot.edge('Bar:p2', 'Foo:data1')
dot.edge('Bew:clk', 'Foo:ex0')

dot.view()
```
