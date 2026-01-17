# Potenza dei test di normalità nel contesto della validazione dei metodi chimici (ISO 17025)

Questo repository contiene una simulazione riproducibile volta a valutare la **potenza del test di Shapiro–Wilk** nel contesto tipico dei rapporti di validazione di metodi chimici, come descritto dalle linee guida **Eurachem**.

## Contesto

Nei rapporti di validazione:
- la precisione e la giustezza vengono spesso stimate su **6–15 misure**;
- è raccomandata l'ispezione dei dati per la presenza di *outlier*;
- in molti casi si applicano test (es. Grubbs) che **assumono normalità dei dati**.

Il test di Shapiro–Wilk viene comunemente utilizzato per verificare tale assunzione.

Questo lavoro mostra, tramite simulazione Monte Carlo, che:
- nel regime di numerosità tipico della validazione,
- anche per deviazioni sostanziali dalla normalità,

il test di Shapiro–Wilk **non possiede potenza sufficiente** per svolgere efficacemente questo ruolo.

## Contenuto del repository

- `report.qmd`  
  Documento Quarto che:
  - descrive il contesto normativo;
  - simula dati da distribuzioni non normali (uniforme e lognormale);
  - stima la potenza del test di Shapiro–Wilk per n = 6–15;
  - produce figure e conclusioni riproducibili.

- `renv/`  
  Ambiente R isolato per garantire la riproducibilità.

## Riproducibilità

Per rigenerare il report localmente:

```r
renv::restore()
quarto::quarto_render("report.qmd")
```

## Messaggio chiave

Nel contesto della validazione di metodi chimici:

- l'assenza di evidenza contro la normalità non è evidenza di normalità;
- l'uso di test sensibili a tale assunzione, su campioni piccoli, è metodologicamente fragile;
- approcci robusti (es. MAD) risultano sufficienti per individuare valori anomali senza ricorrere all'assunzione di normalità.