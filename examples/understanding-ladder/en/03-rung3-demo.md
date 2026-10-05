# Rung 3 (English): utilization vs latency

**Request:** Why does server latency explode once utilization passes ~80%? Explain it the clearest way.

**Rung choice:** the core is "change utilization, watch latency". A slider beats any amount of text. Rung 3.

The output is a single-file HTML page with every rung side by side (demo mode):

- Live: <https://changwenc.github.io/understanding-ladder/docs/demo/?lang=en>
- Source: [docs/demo/index.html](../../../docs/demo/index.html)

Start on tab **3 Page** and drag utilization from 0.9 to 0.95: five more points, double the latency.
