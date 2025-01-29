# 🍕 Esercitazione: Implementazione Backend e Frontend per una Pizzeria

## 📌 Introduzione
Questa esercitazione riguarda lo sviluppo di un'applicazione per una pizzeria che ha appena aperto una nuova sede a **Noventa**. L'obiettivo è creare un sistema per attirare nuovi clienti, includendo un **backend** per la gestione dei dati e un **frontend** per l'interazione utente.

---

## 🛠️ Backend

### 🔧 Tecnologie suggerite
- **Linguaggio:** Node.js (Express) o Python (Django/FastAPI)
- **Database:** PostgreSQL o MongoDB (a seconda delle necessità di relazionalità dei dati)
- **Autenticazione/Autorizzazione:** JWT o OAuth2 (se richiesto per ruoli come amministratore)
- **Test API:** Swagger/OpenAPI per documentazione, Postman per test manuale

### 🏛️ Design Pattern
Si utilizza il design pattern **Repository-Service-Controller**:
- **Repository:** Gestisce l'accesso al database
- **Service:** Contiene la logica di business
- **Controller:** Gestisce le chiamate HTTP e le risposte

### 📂 Modelli di dati

#### **Pizza 🍕**
```json
{
    "id": "uuid",
    "nome": "Margherita",
    "ingredienti": ["mozzarella", "pomodoro", "basilico"],
    "categoria": "pizza",
    "prezzo": 8.50,
    "stagionale": false
}
```

#### **Categoria 📂**
```json
{
    "id": "uuid",
    "nome": "pizza"
}
```

#### **Ordine 📝**
```json
{
    "id": "uuid",
    "data": "2025-01-20",
    "ora": "20:00",
    "pizze": ["id_pizza_1", "id_pizza_2"],
    "bevande": ["id_bevanda_1"],
    "fritti": ["id_fritto_1"],
    "totale": 17.00
}
```

#### **Bevande 🥤**
```json
{
    "id": "uuid",
    "nome": "Coca Cola",
    "prezzo": 2.50
}
```

#### **Fritti 🍟**
```json
{
    "id": "uuid",
    "nome": "Patatine Fritte",
    "prezzo": 3.50
}
```

### 🌐 Chiamate API

#### 📜 **Menu**
1. **GET /menu** → Visualizza il menu (opzione per includere o escludere pizze stagionali).
2. **GET /menu/search** → Ricerca filtrata nel menu (nome, prezzo massimo, stagionale, categoria).
3. **GET /pizza-del-mese** → Restituisce la pizza del mese.

#### 🍕 **Gestione Pizze**
4. **POST /menu/pizza** → Aggiunge una nuova pizza *(validazioni: nome non duplicato, ingredienti unici)*.
5. **PUT | PATCH /menu/pizza/:id** → Modifica una pizza esistente.
6. **DELETE /menu/pizza/:id** → Elimina una pizza *(verifica dipendenze con ordini)*.

#### 📂 **Gestione Categorie**
7. **POST /menu/categoria** → Aggiunge una nuova categoria *(validazione: nome univoco)*.
8. **PUT | PATCH /menu/categoria/:id** → Modifica una categoria esistente.
9. **DELETE /menu/categoria/:id** → Elimina una categoria *(verifica che non contenga elementi associati)*.

#### 📝 **Gestione Ordini**
10. **POST /ordini** → Salva un nuovo ordine *(validazioni: conferma disponibilità prodotti, calcolo prezzo)*.

#### 🥤 **Gestione Bevande**
11. **POST /menu/bevanda** → Aggiunge una nuova bevanda *(validazione: nome non duplicato)*.

#### 🍟 **Gestione Fritti**
12. **POST /menu/fritto** → Aggiunge un nuovo fritto *(validazione: nome non duplicato)*.

---

## 🎨 Frontend

### 🔧 Tecnologie suggerite
- **Framework:** React.js (con TypeScript)
- **Stato globale:** Redux o Context API
- **Chiamate API:** Axios o Fetch API

### 📄 Pagine

#### **🏠 Home**
- Breve descrizione del locale, offerte attuali.
- Sezione per promuovere la "Pizza del mese".
- Pulsanti di navigazione per menu e ordinazione.

#### **📋 Menu**
- Generato dinamicamente tramite API `/menu`.
- Possibilità di filtrare *(stagionale, categoria)*.
- Visualizza nome, prezzo e ingredienti.

#### **🍕📅 Pizza del mese**
- Dettagli della pizza del mese (API `/pizza-del-mese`).
- Sezione per promuovere il concept o sconti.

#### **👥 Chi siamo**
- Informazioni sulla pizzeria, storia, foto.

#### **💼 Lavora con noi**
- Form per inviare candidature con campi: **nome, email, posizione desiderata, messaggio**.

#### **🛒 Effettua un'ordinazione**
- Form per selezionare prodotti dal menu.
- Riepilogo ordine con calcolo del totale.
- Invio dell'ordine tramite API `/ordini`.

### 🧭 Navbar
- **Home** 🏠
- **Menu** 📋
- **Pizza del mese** 🍕📅
- **Chi siamo** 👥
- **Lavora con noi** 💼
- **Effettua un'ordinazione** 🛒

---
