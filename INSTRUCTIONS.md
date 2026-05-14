# Racing Calendars - instrucciones de mantenimiento

Este proyecto proporciona ficheros ICS con el calendario de MotoGP y F1 para 2026.

## Objetivo

Mantener actualizados los calendarios:

- `motogp.ics`
- `f1.ics`

Al inicio de temporada, cada Gran Premio puede estar representado por un unico evento global de dia completo.

Cuando se publiquen los horarios de un Gran Premio, el calendario correspondiente debe actualizarse para sustituir ese evento global por eventos concretos de cada sesion.

## Flujo de actualizacion

El usuario pasara los horarios durante la semana del Gran Premio.

Con esos horarios:

1. Localizar en el fichero ICS correspondiente el evento global de dia completo del Gran Premio.
2. Eliminar ese evento global.
3. Crear un evento por cada sesion publicada.
4. Incorporar el fichero ICS actualizado a las fuentes del proyecto.

## Convenciones de eventos

Cada evento debe incluir:

- `UID` estable siguiendo el patron existente en el fichero.
- `DTSTAMP`.
- `DTSTART` y `DTEND` en UTC.
- `SUMMARY` con emoji, categoria, Gran Premio y sesion.
- `DESCRIPTION` con categoria, Gran Premio, temporada y sesion.
- `STATUS:CONFIRMED`.

## Emojis por categoria

- MotoGP: `🏍️`
- F1: `🏎️`

Ejemplos:

```ics
SUMMARY:🏍️ MotoGP - GP Tailandia (Practice)
DESCRIPTION:MotoGP GP Tailandia 2026 - Practice
```

```ics
SUMMARY:🏎️ F1 - GP Australia (Qualifying)
DESCRIPTION:F1 GP Australia 2026 - Qualifying
```

## Duraciones estimadas

Si el horario publicado no incluye hora de finalizacion, calcular `DTEND` a partir del tipo de sesion usando una duracion estimada coherente con los eventos ya existentes.

Referencias habituales:

- F1 Practice / Free Practice: 60 minutos.
- F1 Qualifying / Sprint Qualifying: 60 minutos.
- F1 Sprint: 60 minutos.
- F1 Grand Prix: 120 minutos.
- MotoGP Free Practice 1: 45-60 minutos segun el horario oficial.
- MotoGP Practice: 60-75 minutos segun el horario oficial.
- MotoGP Free Practice 2: 30 minutos.
- MotoGP Qualifying 1: 15 minutos.
- MotoGP Qualifying 2: 15 minutos.
- MotoGP Sprint: 45 minutos.
- MotoGP Warm-up: 10 minutos.
- MotoGP Grand Prix: 90 minutos.

Cuando haya duda, mantener la convencion ya usada en el calendario correspondiente.

## Notas

- No anadir eventos duplicados para un mismo Gran Premio y sesion.
- Mantener el estilo y el orden cronologico del fichero existente.
- Respetar cambios previos del usuario y no reordenar o reformatear eventos no relacionados.
