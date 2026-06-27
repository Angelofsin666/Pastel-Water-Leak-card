[README(3).md](https://github.com/user-attachments/files/29403733/README.3.md)
# Pastel Water Leak Card

Custom Lovelace card per Home Assistant per il monitoraggio di sensori di
perdita acqua, in stile pastello coerente con le altre card Pastel della
stessa dashboard.

## Funzionalità

- Box riepilogo con illustrazione SVG (goccia stilizzata) e conteggio
  "X/Y perdite rilevate" + barra di progresso.
- Righe sensore cliccabili: il tap apre il popup "more-info" nativo di Home
  Assistant (stato attuale + grafico storico).
- **Una perdita rilevata è sempre evidenziata in rosso fisso**,
  indipendentemente dal colore di base scelto: è un'informazione di
  sicurezza critica e deve risaltare sempre allo stesso modo.
- Colore di base della card personalizzabile (8 tonalità pastello) tramite
  editor visuale.

## Installazione

### Tramite HACS
1. HACS → Frontend → menu (⋮) → **Repository personalizzati**
2. Aggiungi l'URL del repository GitHub, categoria "Lovelace"
3. Cerca "Pastel Water Leak Card" e installala

### Manuale
1. Copia `pastel-water-leak-card.js` in `config/www/`
2. Aggiungi la risorsa in **Impostazioni → Dashboard → Risorse**:
   - URL: `/local/pastel-water-leak-card.js`
   - Tipo: **JavaScript Module** (obbligatorio: il file usa `import`
     dinamici a livello principale)

## Configurazione (YAML)

```yaml
type: custom:pastel-water-leak-card
title: Perdite Acqua
subtitle: Zona Notte
icon: mdi:water-alert
color: blue
show_progress_bar: true
entities:
  - entity: binary_sensor.perdita_doccia
    name: Perdita Doccia
```

Puoi anche configurarla interamente dall'editor visuale dalla dashboard.

### Colori disponibili
`amber` · `blue` · `green` · `pink` · `purple` · `red` · `teal` · `orange`

## Note tecniche

- Compatibile con qualsiasi `binary_sensor` con stato `on`/`off`
  (tipicamente `device_class: moisture`).
- Carica `lit-element`/`lit-html` da CDN per stabilità nel tempo.
