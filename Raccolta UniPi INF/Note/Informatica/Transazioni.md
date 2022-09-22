# Transazioni

### Transazioni

le transazioni sono un meccanismo per recuperare fare l undo  di un set di dati toccati nella transazione stessa lasciarli in uno inconsistente. realizato mantenendo una copia interna dei dati e lavorando su quelli

ha un interfaccia di questo tipo

- **BeginTransaction()**: è il punto di inizio dove viene salvato lo stato dei dati al inizio della transazione
- **EndTransaction()**: il punto di fine transazione in cui se è andata buon termine questa esegue il commit sui dati altrimenti RollBack
- **Commit()**: salva i dati modificati nella transazione
- **RollBack()**: ripristina lo stati dei dati a come se la transazione non fosse mai iniziata
