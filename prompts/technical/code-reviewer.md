# Code Review Assistant

**Categorie**: technical  
**Moeilijkheidsgraad**: Intermediate  
**Geschatte tijd**: 5-15 minuten

## 📋 Context
Ideaal voor het verkrijgen van gedetailleerde en constructieve code reviews. Werkt voor alle programmeertalen en helpt bij het identificeren van bugs, performance issues, security vulnerabilities en code quality verbeteringen.

## 🎯 Doel
Krijg een professionele code review met concrete verbeteringsvoorstellen, best practices en uitleg van potentiële problemen.

## 🤖 Prompt
```
Je bent een senior software engineer met 10+ jaar ervaring. Voer een grondige code review uit op de volgende code.

CONTEXT:
- Programmeertaal: [JavaScript/Python/PHP/Java/etc.]
- Project type: [web app/API/library/script/etc.]
- Doelgroep: [intern team/open source/productie/prototype]
- Performance requirements: [hoog/normaal/laag]

CODE VOOR REVIEW:
```
[Plak hier je code]
```

Geef feedback op:

1. **🐛 BUGS & ERRORS**
   - Syntaxfouten
   - Logische fouten
   - Edge cases die niet afgehandeld worden

2. **🔒 SECURITY**
   - Potentiële security vulnerabilities
   - Input validation
   - Data sanitization

3. **⚡ PERFORMANCE**
   - Inefficiënte algoritmes
   - Memory leaks
   - Database query optimalisaties

4. **📚 CODE QUALITY**
   - Leesbaarheid en maintainability
   - Naming conventions
   - Code structure en organization

5. **✅ BEST PRACTICES**
   - Industry standards
   - Framework-specific recommendations
   - Testing suggestions

Voor elk probleem:
- Leg uit WAAROM het een probleem is
- Geef een CONCRETE oplossing
- Toon de VERBETERDE code
- Schat de PRIORITEIT in (Hoog/Medium/Laag)

Sluit af met:
- Overall code quality score (1-10)
- Top 3 prioriteiten om aan te pakken
- Positive feedback over goede delen
```

## 📖 Voorbeeld

### Input
```
CONTEXT:
- Programmeertaal: JavaScript
- Project type: E-commerce web app
- Doelgroep: Productie
- Performance requirements: Hoog

CODE VOOR REVIEW:
```javascript
function getUserData(userId) {
    let user = database.query("SELECT * FROM users WHERE id = " + userId);
    if (user) {
        user.password = "****";
        return user;
    }
    return null;
}

function processOrder(order) {
    var total = 0;
    for (var i = 0; i < order.items.length; i++) {
        total += order.items[i].price * order.items[i].quantity;
    }
    
    if (total > 0) {
        // Save to database
        database.query("INSERT INTO orders VALUES (" + order.id + ", " + total + ")");
        return { success: true, total: total };
    }
}
```
```

### Expected Output
```
## 🔍 CODE REVIEW RESULTAAT

### 🐛 BUGS & ERRORS

**HOGE PRIORITEIT - SQL Injection Vulnerability**
- **Probleem**: Direct concatenation van user input in SQL queries
- **Risico**: Volledige database compromise mogelijk
- **Oplossing**: Gebruik prepared statements

```javascript
// ❌ Kwetsbaar
let user = database.query("SELECT * FROM users WHERE id = " + userId);

// ✅ Veilig
let user = database.query("SELECT * FROM users WHERE id = ?", [userId]);
```

**MEDIUM PRIORITEIT - Geen error handling**
- **Probleem**: Database errors worden niet afgehandeld
- **Risico**: App crash bij database problemen
- **Oplossing**: Voeg try-catch toe

### 🔒 SECURITY

**HOGE PRIORITEIT - Wachtwoord in response**
- **Probleem**: Wachtwoord wordt vervangen maar mogelijk nog steeds gelogd
- **Oplossing**: Exclude password in query

```javascript
// ✅ Veiliger
let user = database.query("SELECT id, username, email FROM users WHERE id = ?", [userId]);
```

### ⚡ PERFORMANCE

**MEDIUM PRIORITEIT - Inefficiënte loop**
- **Probleem**: Oude for-loop syntax
- **Oplossing**: Gebruik moderne array methods

```javascript
// ✅ Beter
const total = order.items.reduce((sum, item) => sum + (item.price * item.quantity), 0);
```

### 📚 CODE QUALITY

**MEDIUM PRIORITEIT - Inconsistente variable declarations**
- Gebruik `const` voor unchanging values, `let` voor changing
- Vermijd `var` in moderne JavaScript

**LAAG PRIORITEIT - Naming conventions**
- `getUserData` is goed, maar `processOrder` zou specifieker kunnen

### ✅ VERBETERDE VERSIE

```javascript
async function getUserData(userId) {
    try {
        const user = await database.query(
            "SELECT id, username, email, created_at FROM users WHERE id = ?", 
            [userId]
        );
        return user || null;
    } catch (error) {
        console.error('Database error:', error);
        throw new Error('Unable to fetch user data');
    }
}

async function calculateOrderTotal(order) {
    if (!order?.items?.length) {
        throw new Error('Invalid order: no items found');
    }
    
    const total = order.items.reduce((sum, item) => {
        if (!item.price || !item.quantity) {
            throw new Error('Invalid item: missing price or quantity');
        }
        return sum + (item.price * item.quantity);
    }, 0);
    
    try {
        await database.query(
            "INSERT INTO orders (id, total, created_at) VALUES (?, ?, NOW())",
            [order.id, total]
        );
        return { success: true, total };
    } catch (error) {
        console.error('Failed to save order:', error);
        throw new Error('Unable to process order');
    }
}
```

## 📊 SCORE & PRIORITEITEN

**Overall Code Quality: 4/10**

**Top 3 Prioriteiten:**
1. 🚨 **Fix SQL Injection** - Kritieke security vulnerability
2. 🔧 **Add Error Handling** - Voorkom app crashes
3. 🛡️ **Remove Password Exposure** - Data privacy verbetering

**Positieve punten:**
- Goede functie naming
- Simpele, begrijpbare logica
- Consistent code formatting
```

## 💡 Tips & Variaties

### Voor verschillende talen:
- **Python**: Focus op PEP 8, list comprehensions, exception handling
- **Java**: Emphasize OOP principles, design patterns, null safety
- **PHP**: Security (SQL injection, XSS), PSR standards, type declarations
- **React**: Component structure, hooks usage, performance optimization

### Specifieke review types:
- **Security-focused**: `Voer vooral een security audit uit...`
- **Performance-focused**: `Focus op performance optimalisaties...`
- **Beginner-friendly**: `Geef uitgebreide uitleg geschikt voor beginners...`
- **Legacy code**: `Dit is legacy code, focus op refactoring mogelijkheden...`

### Als de review te oppervlakkig is:
- Vraag om specifieke examples van betere code
- Voeg meer context toe over het project
- Specificeer welke aspecten het belangrijkst zijn
- Vraag om prioritering van de gevonden issues

## 🧪 Getest met
- [x] ChatGPT (GPT-4)
- [x] Claude (Sonnet)
- [x] Gemini Pro
- [ ] GitHub Copilot

## 🏷️ Tags
`code-review` `technical` `debugging` `security` `performance` `best-practices` `quality` `development`

## 📚 Gerelateerde Prompts
- [Bug Hunter](./bug-hunter.md)
- [Security Audit Assistant](./security-audit.md)
- [Performance Optimizer](./performance-optimizer.md)
- [Documentation Generator](./documentation-generator.md)

---
**Auteur**: WorkFlo AI Team  
**Datum**: 2025-05-31  
**Versie**: 1.0
