# **Guía de Diseño UI/UX – Super‑App Delivery (v1.0)**

**Visión:** Crear una experiencia *friendly* y **moderna**, coherente en Cliente, Admin Panel y Repartidor, usando un **tema dual blanco & negro** con acento **\#F07167**.

---

## **1\. Identidad Visual**

| Elemento | Directriz |
| ----- | ----- |
| **Logo** | Versión principal monocromática con acento **\#F07167** (gota/word‑mark). Clear‑space \= ½ altura del icono. Tamaño mínimo 32 px. |
| **Fondo por defecto** | ‑ Dark mode: **\#070707**  ‑ Light mode: **\#FFFFFF** |
| **Fotografía** | Imágenes vibrantes, alto contraste, enfocadas en cercanía/servicio. Borders 8 px radius. |
| **Ilustración** | Estilo lineal 2 px y relleno suave \#F07167 10 % opacity. |

---

## **2\. Paleta de Color (Tokens)**

| Token | Hex | Uso principal |
| :---- | :---- | :---- |
| `--c‑accent` | **\#F07167** | CTAs, links activos, toggles ✔️ |
| `--c‑black` | **\#070707** | Textos en Dark, backgrounds profundos |
| `--c‑white` | **\#FAFAFA** | Textos en Light, surfaces elevadas |
| `--c‑gray‑900..50` | \#1A1A1A · \#2B2B2B · \#4C4C4C · \#6E6E6E · \#BFBFBF · \#E6E6E6 | Bordes, estados, texto secundario |
| Feedback‑Success | \#4ADE80 | Mensajes positivos |
| Feedback‑Error | \#EF4444 | Errores & validaciones |

**Accesibilidad:** Mantener ≥ 4.5:1 de contraste; ajustar opacidades si es necesario.

---

## **3\. Tipografía**

* **Familia:** *Inter*, fallback `system-ui`.  
* **Escala modular (1.25):** 32‑24‑20‑16‑14‑12 px.  
* **Pesos usados:** 400 / 500 / 700\.  
* **Tracking:** 0 – ‑0.25 pt según tamaño.

### **Ejemplo jerarquía (Dark)**

H1 32 /40  \#FFFFFF  
H2 24 /32  \#FFFFFF  
Body 16 /24  \#E6E6E6  
Caption 12 /16  \#BFBFBF  
---

## **4\. Layout & Espaciado**

* **Grid base:** 4‑pt; múltiplos (4‑8‑12‑16…).  
* **Breakpoints (Tailwind):** `sm` 640 px, `md` 768 px, `lg` 1024 px, `xl` 1280 px.  
* **Cards/Sheets:** radius `rounded‑2xl` (24 px), shadow `md` (elevación media).  
* **Safe‑areas:** 16 px paddings laterales móviles.

---

## **5\. Component Library (Shadcn \+ Tailwind tokens)**

| Componente | Estados | Puntos clave |
| :---- | :---- | :---- |
| **Button** (`primary`) | normal, hover (lighten 6 %), active (\#C85F58), disabled (opacity 40 %) | Radius full, texto 14 /semibold white /black según tema |
| **Input** | default, focus (border‑accent 2 px), error (red‑500) | Label 12 /medium; helper 12 /regular |
| **Card** | default, hover (translate‑y‑1, shadow‑lg) | Padding 6; icon opcional 24 px |
| **Bottom Nav (Cliente)** | 4 items max, íconos 24 px, label 10 px | Activo: color accent, fondo black 12 % overlay |
| **FAB** | 56 px, sombra xl, icono Lucide `shopping-cart` | Badge red‑500 /12 px |
| **Badge/Chip** | radius full, texto 12 px | Color accent o gray styles |

### **Tokens Tailwind (`tailwind.config.ts`)**

colors: {  
  accent: '\#F07167',  
  black: '\#070707',  
  white: '\#FAFAFA',  
  gray: {  
    900:'\#1A1A1A', 800:'\#2B2B2B', 700:'\#4C4C4C', 600:'\#6E6E6E',  
    300:'\#BFBFBF', 100:'\#E6E6E6'  
  }  
}  
---

## **6\. Iconografía & Ilustraciones**

* **Set:** Lucide React. Stroke 1.5 px en dark, 2 px en light.  
* **Tamaño base:** 24 px.  
* **Animaciones:** Opacidad → 100 ms; escala al presionar 95 %.

---

## **7\. Motion & Micro‑interactions**

* **Librería:** Framer Motion.  
* **Duraciones:** entradas 250 ms, salidas 200 ms.  
* **Eases:** `easeOutQuad`.  
* **Ejemplos:**  
  * FAB aparece con fade+scale.  
  * Snackbar desliza desde bottom 16 px.

---

## **8\. Accesibilidad**

1. Navegación por teclado completa.  
2. Focus‑ring visible (\#F07167 outline 2 px offset 2).  
3. Textos `<H1‑H6>` semánticos.  
4. `aria‑label` en icon‐buttons.

---

## **9\. Aplicaciones específicas**

### **9.1 Cliente PWA**

* **Dark mode** default; light opcional.  
* **TopNav transparente** → fill al scroll \>64 px.  
* **Bottom Nav** sticky.  
* **Cards tienda**: width 72 %, scroll‑snap.

### **9.2 Admin Panel**

* **Light mode** default; dark toggle.  
* **Sidebar** collapsible 72 → 240 px.  
* **Data Tables** zebra gray‑100 rows; selección row accent outline.

### **9.3 Repartidor PWA**

* **Dark mode** forced (outdoor legibility).  
* **Toggle Online**: big switch accent.  
* **Order steps** timeline vertical accent bar.

---

## **10\. Diseño de Interacción Clave**

| Flujo | Punto WOW | Métrica UX |
| :---- | :---- | :---- |
| Onboarding dirección | Mapa mini y pin animado pulse | \< 30 s completion |
| Checkout | Resumen sticky con “Pagar $” slide‑up sheet | \< 3 errors/session |
| Admin → Cambiar estado orden | Toast confirmación con icono check | NPS \> 80 |

---

## **11\. Entrega & Próximos Pasos**

1. Integrar tokens en Tailwind \+ Shadcn.  
2. Crear Storybook con 30 \+ componentes.  
3. Prototipo Figma de pantallas prioritarias (Home, Checkout, Admin dashboard, Driver order flow).  
4. Pruebas WCAG AA.

---

*Diseñado por "El mejor diseñador del mundo" – Abr 2025\.*

