# Viñales on Horseback

A bilingual, responsive website developed for a real horseback riding business in Viñales, Cuba.

The website helps visitors learn about the horseback riding experience and provides direct access to the business through WhatsApp, Airbnb, Tripadvisor and social media.

## Live Website

**[Visit Viñales on Horseback](https://victorcubapri-sys.github.io/vinales-on-horseback/)**

## About the Project

This is a real-world web development project created for my father's horseback riding business in Viñales, Cuba.

The goal was to create a professional, accessible and mobile-friendly website where potential customers can discover the experience, view photos, learn about the tour and easily contact the business.

The website is available in both Spanish and English to serve local and international visitors.

## Features

* Responsive design for desktop, tablet and mobile devices
* Spanish and English content
* WhatsApp contact and booking flow
* Airbnb and Tripadvisor integration
* Image gallery with lightbox
* Client-side form validation
* Accessible navigation and form labels
* Keyboard-friendly navigation
* Reduced-motion support
* Custom 404 page
* Basic SEO configuration
* `robots.txt` and `sitemap.xml`
* LocalStorage for interface preferences
* Content Security Policy and security headers

## Technologies

* HTML5
* CSS3
* JavaScript
* Git
* GitHub
* GitHub Pages

## Contact & Booking Flow

The website includes a contact form that validates the visitor's information in the browser.

After validation, JavaScript generates a pre-filled WhatsApp message containing the booking information. The visitor can review the message before deciding whether to send it.

The website does not store booking requests on a server because it is a static website.

## Accessibility

Accessibility was considered throughout the development of the website.

The project includes:

* Semantic HTML
* Accessible form labels and error messages
* Keyboard navigation
* Skip-to-content link
* Alternative text for images
* Visible focus states
* `prefers-reduced-motion` support

## SEO

The project includes basic SEO features such as:

* Descriptive page titles
* Meta descriptions
* Open Graph metadata
* Semantic HTML structure
* `robots.txt`
* `sitemap.xml`

## Security

The project includes several frontend and hosting security measures:

* Content Security Policy
* `X-Content-Type-Options`
* `X-Frame-Options`
* `Referrer-Policy`
* `Permissions-Policy`
* HTTPS deployment
* `rel="noopener noreferrer"` for external links opened in new tabs
* No API keys or private credentials exposed in the frontend

Because the project is a static website, these measures do not replace server-side security.

If a backend is added in the future, server-side validation, rate limiting, CSRF protection and server-side anti-spam measures should also be implemented.

## Deployment

The website is deployed using **GitHub Pages**.

No build system or framework is required. The project consists of static HTML, CSS, JavaScript and image assets.

## What I Learned

This project gave me practical experience developing and deploying a website for a real business.

Through the project, I practiced:

* Building responsive layouts
* Working with the DOM using JavaScript
* Client-side form validation
* Integrating external services
* Responsive image handling
* Accessibility fundamentals
* Basic SEO
* Git and GitHub
* Static website deployment
* Frontend security considerations

## Future Improvements

Possible future improvements include:

* Further performance optimization
* Lighthouse testing and improvements
* Automated testing
* Improved image optimization
* A dedicated backend or form service
* Additional accessibility testing
* Privacy-focused analytics if needed

## Author

**Victor Manuel Arencibia Solano**

Junior Web Developer

[GitHub](https://github.com/victorcubapri-sys)
