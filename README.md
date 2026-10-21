# AR Tourism Explorer

A generic PHP/MySQL platform for connecting tourism posters with interactive augmented-reality stories. It is designed for XAMPP, shared hosting and HTTPS-enabled mobile browsers.

## Current phase

Phase 1 includes the project foundation, responsive public homepage, AR entry screen, PDO configuration helpers, and the normalized MySQL schema for destinations, attractions, posters, hotspots, users and activity logs.

The browser AR page currently explains the target workflow. MindAR target compilation and authenticated admin CRUD are planned as the next implementation slices; a browser cannot compile `.mind` files through PHP alone without a server-side MindAR compiler or a supported build service.

## Setup

1. Copy the project into `C:\xampp\htdocs\AR Torism`.
2. Start Apache and MySQL in XAMPP.
3. Open phpMyAdmin and import `database/database.sql`.
4. Review credentials in `includes/config.php`.
5. Open `http://localhost/AR%20Torism/` or use the folder name configured by Apache.
6. For phone camera access, serve the site over HTTPS. `localhost` is treated as a secure development context by modern browsers, but a LAN IP generally needs HTTPS.

## Technology

- PHP 8.3+
- MySQL 8+
- PDO with emulated prepares disabled
- Bootstrap 5, Font Awesome and Google Fonts
- Vanilla JavaScript
- MindAR Image Tracking and Three.js in the AR implementation phase

## Security direction

All user-facing output goes through escaping helpers, database access is centralized through PDO, and uploaded files should be stored outside executable PHP paths with MIME, extension, size and image-dimension validation. Admin forms must add session authentication and CSRF tokens before production use.

## AR target workflow

An administrator uploads a high-quality poster, configures normalized hotspot coordinates, then compiles the image target to an associated `.mind` file. The visitor AR page loads only a ready target and its hotspot data. Replacing a poster invalidates its target status.
