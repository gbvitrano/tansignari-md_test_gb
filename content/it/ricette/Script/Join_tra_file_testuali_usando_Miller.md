---
title: "Join tra file testuali usando Miller"
linkTitle: "Join tra file testuali usando Miller"
date: 2019-04-18
description: >
 Come realizzare una JOIN tabellare tra file testuali usanso Miller.
tags:
  - Miller
  - CSV
  - TSV
  - Join
  - script
  - bash
issue: [60]
autori: ["Totò Fiandaca"]
chefs: ["Andrea Borruso"]
---

---

**Caso d'uso:** Partendo da due file di testo, con diverso numero di colonne, fare un `join` tra il campo 3 del primo e 1 del secondo file mantenendo solo alcuni campi e non tutti, tenendo presente che il primo file è un CSV con intestazione e il secondo un TSV senza intestazione.

## script

```bash
mlr --icsv --onidx --ofs "\t" cat layer.csv >layer_t.tsv
mlr --nidx --fs "\t" join -j 3 -r 1 --rp r -f out_regioni_xpath.tsv then cut -f 1,r2 layer_t.tsv >out.tsv
```

## osservazioni

- `prima riga script`: trasforma il file CSV con intestazione in un file TSV senza intestazione;
- `seconda riga`: mette in join i due file testuali usando, come colonna comune, la 3 del primo e 1 del secondo, infine conserva solo le colonne 1 e r2 del file di output (per maggiori dettagli leggere [issue](https://github.com/opendatasicilia/tansignari/issues/60#issuecomment-483668171)).

## dati di esempio

- [primo file testuale CSV](https://github.com/opendatasicilia/tansignari/files/3084976/layer.zip)
- [secondo file testuale TSV](https://github.com/opendatasicilia/tansignari/files/3084977/out_regioni_xpath.zip)

## Riferimenti utili

- [**Miller**](https://github.com/johnkerl/miller)