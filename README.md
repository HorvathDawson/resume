### Why Use HTML Instead of Word or LaTeX for Creating a Resume?

When creating a resume, many people default to using tools like Word or LaTeX. However, HTML and CSS offer distinct advantages that make them an appealing choice for building and maintaining a resume:

1. **Web Compatibility**: HTML is the standard for web content, making it easy to integrate your resume into a personal website, portfolio, or online profile. This ensures consistency across both digital and printable versions, so your resume will look great in both formats.

2. **Flexibility with Styling**: HTML and CSS provide unparalleled control over layout and design. With features like flexbox and grid, you can create responsive, dynamic layouts tailored to your personal style. Custom media queries also allow you to optimize your resume for different devices and print formats, something that would be more difficult to achieve in Word or LaTeX.

3. **Cross-Platform Consistency**: HTML ensures that your resume looks consistent across various platforms. Unlike Word or LaTeX, which may behave differently depending on the device or software version, HTML provides a uniform appearance when viewed in different browsers or printed out. This helps maintain a professional, polished look no matter where it's viewed.


### Creating a Styled A4 Document Layout with CSS

This tutorial will guide you on how to create an A4-sized page layout using CSS, suitable for printing or document generation. We will set up custom page dimensions, styles, and positioning to ensure everything looks good when rendered in a print-friendly environment.

### 1. **HTML Structure**

The basic structure for your document will consist of the `<html>`, `<head>`, and `<body>` elements. We'll also use the `<page>` tag to define the A4 page sections.

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        /* Page styles go here */
    </style>
</head>
<body>
    <page size="A4">
        <!-- Content of the page goes here -->
    </page>
</body>
</html>
```

### 2. **Basic Page Setup**

#### Setting up the body and page styles:
We will define the body of the document and the page's layout. The body will have a background color and a fixed size of A4. Additionally, we will set the margin to `auto` to center it on the page.

```css
body {
    background: rgb(204, 204, 204);  /* Set a light gray background */
    width: 21cm;                      /* A4 width */
    height: 29.7cm;                   /* A4 height */
    margin: 0 auto;                   /* Center the body */
    font-family: 'Roboto', sans-serif; /* Apply the Roboto font globally */
}

page {
    background: white;                /* Set the background of the page to white */
    display: block;                    /* Set the page to display as a block */
    margin: 0 auto;                    /* Center the page */
    margin-bottom: 0.5cm;              /* Add some space at the bottom */
    position: relative;                /* Allow absolute positioning of inner elements */
}
```

#### Setting A4 size for the page:
This rule ensures that any `<page>` element with the `size="A4"` attribute will be styled with the correct A4 dimensions.

```css
page[size="A4"] {
    width: 21cm;
    height: 29.7cm;
}
```

#### Using the `@page` rule:
The `@page` rule is used to control page margins for printing. Here, we set the page size to A4 and remove any default margins.

```css
@page {
    size: 21cm 29.7cm; /* A4 size */
    margin: 0mm;        /* No margins for the page */
}
```

### 3. **Footer Design**

You can customize the footer to include elements like background shapes, text, and icons. Here's how you can style a footer that spans the width of the page, with various design elements:

```css
footer {
    width: 100%;
    height: 4.25cm;
    background-color: transparent;
    position: absolute;
    bottom: 0;
    overflow: hidden;
    z-index: 2;
}

footer .foot-front {
    width: 100%;
    height: 100%;
}

footer .foot-front .left {
    width: 17cm;
    height: 5cm;
    z-index: 1;
    transform: rotate(7deg);
    background-color: var(--primary-color);
    box-shadow: 0 0 0.317cm -0.105cm #000;
    position: absolute;
    bottom: -2.40cm;
    left: -2cm;
}

footer .foot-front .right {
    width: 10cm;
    height: 5cm;
    z-index: 2;
    transform: rotate(28deg);
    background-color: var(--primary-color);
    position: absolute;
    bottom: -5.51cm;
    left: 13.48cm;
}
```

### 4. **Content Layout**

For your document content, you may want to divide it into sections or columns. This can be easily achieved using flexbox or grid layout. Here’s how you can set up a basic two-column layout for your document body:

```css
.cv-body {
    display: flex;
    flex-direction: row;    /* Place content side by side */
    width: 100%;
    height: 100%;
    margin: 0;
    padding: 0;
}

.right-column {
    background-color: var(--primary-color);
    height: 100%;
    padding-top: 0.25cm;
    width: 26%;              /* Adjust this for the width of the right column */
}

.left-column {
    background-color: transparent;
    height: 100%;
    padding-top: 0.25cm;
    margin-left: 0.25cm;
    margin-right: 0.25cm;
    width: 74%;              /* Adjust this for the width of the left column */
}
```

### 5. **Text Styles**

For headers and text, we use custom font sizes, margins, and padding to control the document's look:

```css
h1 {
    font-family: 'Roboto', sans-serif;
    font-weight: 300;
    font-size: 1.2cm;
    transform: scale(1, 1.15);  /* Adjust vertical scaling */
    margin-bottom: 0.2cm;
    margin-top: 0.2cm;
    text-transform: uppercase;
}

h2 {
    font-size: 0.65cm !important;
}

h3 {
    font-family: 'Roboto', sans-serif;
    padding-left: 0.3cm;
}
```

### 6. **Lists and Sections**

To style lists and other structured content like experiences or education:

```css
.experience h2 {
    border-left: 0.05cm solid rgba(0, 0, 0, 0.1);
    padding-left: 0.1cm;
}

.experience>ul>li ul {
    padding-left: 0.5cm;
    list-style-type: disc;
}

.experience>ul {
    list-style-type: none;
    padding-left: 0;
}

.experience>ul>li {
    position: relative;
    margin: 0;
    padding-bottom: 0.2cm;
    padding-left: 0.5cm;
}

.experience>ul>li:before {
    background-color: var(--primary-color);
    width: 0.025cm;
    content: '';
    position: absolute;
    top: 0.15cm;
    bottom: -0.2cm;
    transform: translatex(-50%);
    left: 0cm;
    margin-left: 0.15cm;
}
```

### 7. **Using Real Unit Dimensions for Printability**

When designing documents for printing, **real unit dimensions** such as **centimeters (cm)** or **millimeters (mm)** are essential. This ensures that your content is sized appropriately for the physical page size, especially when printed on an A4 page. Using real units allows for better control over layout, margins, and positioning, preventing elements from being misaligned or overflowing.

For example:
```css
/* Set width and height in real units (cm) */
div {
    width: 10cm;  /* Use cm for accurate measurement */
    height: 5cm;
    padding: 0.5cm;
}

/* Set font sizes in real units (cm or mm) */
h1 {
    font-size: 1.2cm;
}

/* Use fixed units for margins */
@page {
    size: 21cm 29.7cm;  /* A4 size */
    margin: 0mm;
}
```

### 8. **Additional Tips for Consistent Printability**

- **Avoid Using Fixed Pixels:** While pixels are great for screen design, they don’t translate well for print layouts. For printing, it's better to use **cm**, **mm**, or **inches** to ensure consistent scaling across various printers.
  
- **Page Breaks:** Use `page-break-before`, `page-break-after`, or `page-break-inside` CSS properties to control where content should break between pages. For example:
  ```css
  .section {
      page-break-before: always;  /* Forces a page break before this section */
  }
  ```

- **Consistent Font Sizes:** Stick to font sizes that are proportional and use real units. Fonts should be large enough to be readable on paper, with 10pt to 12pt being a typical range for body text.

- **Margins and Padding:** Always account for printer margins. Define consistent margins (using real units like cm or mm) to prevent clipping or overflow on different printers.

- **Testing Across Devices:** Even with perfect CSS rules, printers can behave differently. Always test your layout on multiple devices to ensure the layout is consistent.

---
