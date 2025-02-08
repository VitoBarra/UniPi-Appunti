---
Course: "[[Intelligenza Artificiale (IA)]]"
Area: "[[Concetti generali del Machine Learning]]"
topic: "[[Intelligenza Artificiale (IA)|Reti neurali]]"
SubTopic: 
tags:
  - IA
  - ML
---
# RNN - Long Short-term Memory (LSTM)
---




è come i [[Reti Neurali Ricorrenti (RNN)|RNN]] ma ogni passaggio ha un suo peso specifico invece di ripetere sempre lo stesso peso.
quindi per $n$ dati su un input si usano $W_i$ da $i =1,\dots,n$ pesi diversi 



Utilizza due [[Funzioni di attivazione|funzioni di attivazione]] la [[Funzione di attivazione - Sigmoide|Sigmoide]] e la [[Funzione di attivazione - TanH|TanH]] 





### Equazioni delle LSTM

Una cella LSTM è definita da tre porte principali:
1. **Porta di ingresso**:
   $$
   i_t = \sigma(W_i x_t + U_i h_{t-1} + b_i)
   $$
2. **Porta di dimenticanza**:
   $$
   f_t = \sigma(W_f x_t + U_f h_{t-1} + b_f)
   $$
3. **Porta di output**:
   $$
   o_t = \sigma(W_o x_t + U_o h_{t-1} + b_o)
   $$

Lo stato della memoria è aggiornato come:

$$
c_t = f_t \odot c_{t-1} + i_t \odot \tanh(W_c x_t + U_c h_{t-1} + b_c)
$$

dove $\odot$ indica il prodotto elemento per elemento. Lo stato nascosto della rete è calcolato come:

$$
h_t = o_t \odot \tanh(c_t)
$$

Le **GRU** semplificano il modello LSTM, combinando le porte di ingresso e di dimenticanza in un'unica porta di aggiornamento.
