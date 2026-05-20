# SPA vs MPA

# SPA (Single Page Application)

## What is SPA?

SPA loads a single HTML page and dynamically updates content without refreshing the full page.

React applications mostly use SPA architecture.

---

## How It Works

- Initial page loads once
- JavaScript handles routing and UI updates
- Only required data/components update

---

## Example

- React
- Angular
- Vue

---

## Advantages

- Faster navigation
- Better user experience
- No full page reload
- Smooth UI transitions

---

## Disadvantages

- Initial load can be heavy
- SEO is difficult without SSR
- More JavaScript dependency

---

## Best Use Cases

- Dashboard
- Social media apps
- Admin panels
- Real-time applications

---

# MPA (Multi Page Application)

## What is MPA?

MPA loads a new HTML page from the server for every route or request.

Traditional websites mostly use MPA architecture.

---

## How It Works

- Every page request reloads the full page
- Server sends new HTML for each route

---

## Example

- Traditional PHP websites
- ASP.NET MVC
- Older e-commerce websites

---

## Advantages

- Better SEO
- Better for large content websites
- Easy server-side rendering

---

## Disadvantages

- Slower navigation
- Full page refresh every time
- Less smooth user experience

---

## Best Use Cases

- News websites
- Blogging platforms
- Large SEO-based websites

---

# Difference Between SPA and MPA

| SPA | MPA |
|---|---|
| Single HTML page | Multiple HTML pages |
| No full page reload | Full page reload |
| Faster navigation | Slower navigation |
| Better user experience | Traditional experience |
| SEO needs SSR support | Better SEO by default |
| React/Vue/Angular | Traditional server apps |

---

# Interview One-Line Answer

> SPA loads a single page and updates content dynamically, while MPA reloads a new page from the server for every request.
```
