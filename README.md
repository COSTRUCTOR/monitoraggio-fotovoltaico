# SolarTech Monitor - Sistema di Gestione Impianti Fotovoltaici

Progetto realizzato per l'esame di stato/modulo di sviluppo web. 
L'applicazione permette il monitoraggio della produzione energetica di diversi parchi solari, integrando dati meteorologici in tempo reale per la manutenzione predittiva.

## 🚀 Funzionalità Principali
- **Dashboard Dinamica**: Visualizzazione delle prestazioni di tutti gli impianti.
- **Integrazione API Meteo**: Recupero automatico dei dati di irraggiamento solare tramite *Open-Meteo API*.
- **Analisi Efficienza**: Calcolo automatico del rendimento percentuale in base alla capacità massima dell'impianto.
- **Sistema Alert**: Notifica visiva di "Alert Efficienza" quando l'irraggiamento è alto ma la produzione è sotto la soglia ottimale.
- **Gestione CRUD**: Inserimento manuale delle letture giornaliere tramite form integrato.

## 🛠️ Tecnologie Utilizzate
- **Frontend**: Next.js 14 (App Router), React, Tailwind CSS.
- **Backend**: Next.js API Routes (Serverless).
- **Database**: MySQL (gestito tramite `mysql2/promise`).
- **Linguaggio**: TypeScript.

📂 Struttura del progetto
Il progetto adotta una struttura Flat-App Router. La directory /app è situata nella root del progetto per massimizzare la velocità di sviluppo e l'accessibilità dei componenti, seguendo le best-practices documentate dal team di Vercel per Next.js 14.

## ⚙️ Configurazione Database
Per far girare il progetto, è necessario importare le seguenti tabelle nel database MySQL:

```sql
CREATE DATABASE esame_fabio_caragliu;
USE esame_fabio_caragliu;

CREATE TABLE impianti (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome_parco VARCHAR(100),
    latitudine DECIMAL(10, 8),
    longitudine DECIMAL(11, 8),
    capacita_max_kw INT
);

CREATE TABLE produzione (
    id INT AUTO_INCREMENT PRIMARY KEY,
    id_impianto INT,
    data DATE,
    kwh_prodotti DECIMAL(10, 2),
    ore_funzionamento DECIMAL(5, 2),
    FOREIGN KEY (id_impianto) REFERENCES impianti(id)
);
