# Floema

A modern, award-worthy website boilerplate featuring smooth page transitions, WebGL effects, and seamless Prismic CMS integration. This starter project is designed to help developers create visually stunning websites with advanced animations and 3D graphics.

## Overview

Floema is a full-stack web application boilerplate that combines the power of Express.js on the backend with a sophisticated frontend featuring GSAP animations and WebGL rendering via OGL. It's specifically built to work with Prismic CMS v6, making it easy to manage content while maintaining exceptional performance and visual appeal.

This project was inspired by Luis Henrique Bizzaro's Awwwards course and has been updated to use the latest web development practices and Prismic v6 API.

## Features

- **Prismic CMS v6 Integration** - Headless CMS with easy content management
- **Smooth Page Transitions** - GSAP-powered animations between pages
- **WebGL Graphics** - 3D effects using OGL (WebGL library)
- **Server-Side Rendering** - Express.js with Pug templating
- **Modern Build Pipeline** - Webpack 5 with development and production configs
- **Hot Module Replacement** - Fast development with live reloading
- **Image Optimization** - Automatic image compression with webpack plugins
- **SCSS Support** - Modern CSS with Sass preprocessing
- **Code Quality Tools** - ESLint and Prettier for consistent code style

## Tech Stack

### Backend
- **Express.js** - Web application framework
- **Pug** - Template engine for server-side rendering
- **Prismic Client v6** - Headless CMS integration
- **Node Fetch** - HTTP requests
- **dotenv** - Environment variable management

### Frontend
- **GSAP** - Professional-grade animation library
- **OGL** - Minimal WebGL library for 3D graphics
- **Normalize Wheel** - Cross-browser mouse wheel normalization
- **Lodash** - Utility library

### Build Tools
- **Webpack 5** - Module bundler
- **Babel** - JavaScript transpiler
- **Sass** - CSS preprocessor
- **Nodemon** - Auto-restart development server
- **Concurrently** - Run multiple npm scripts simultaneously

## Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v14 or higher)
- **npm** (v6 or higher)
- **Prismic Account** - Sign up at [prismic.io](https://prismic.io)

## Installation

1. **Clone or download this repository**

```bash
git clone <repository-url>
cd floema
```

2. **Install dependencies**

```bash
npm install
```

3. **Set up environment variables**

Create a `.env` file in the root directory:

```env
PRISMIC_ENDPOINT=https://your-repo-name.prismic.io/api/v2
PRISMIC_ACCESS_TOKEN=your_access_token_here
PORT=8005
```

4. **Configure your Prismic repository**

You'll need to create the following custom types in your Prismic repository:

- **meta** (Single Type) - Site metadata
- **home** (Single Type) - Homepage content
- **about** (Single Type) - About page content
- **collection** (Repeatable Type) - Product collections
- **product** (Repeatable Type) - Individual products

## Project Structure

```
floema/
├── app/                    # Frontend JavaScript entry point
│   └── index.js           # Main application file
├── app.js                 # Express server configuration
├── styles/                # SCSS stylesheets
│   └── index.scss        # Main stylesheet
├── views/                 # Pug templates
│   ├── _includes/        # Reusable template components
│   │   ├── head.pug      # HTML head section
│   │   ├── layout.pug    # Base layout template
│   │   ├── navigation.pug # Navigation component
│   │   ├── preloader.pug # Loading animation
│   │   └── scripts.pug   # Script includes
│   ├── pages/            # Page templates
│   │   ├── home.pug      # Homepage
│   │   ├── about.pug     # About page
│   │   ├── collections.pug # Collections page
│   │   └── detail.pug    # Product detail page
│   └── index.pug         # Main template
├── shared/               # Shared utilities and assets
├── webpack.config.js     # Base webpack configuration
├── webpack.config.development.js # Development config
├── webpack.config.build.js # Production config
├── .eslintrc.js         # ESLint configuration
├── .prettierrc          # Prettier configuration
├── .editorconfig        # Editor configuration
└── package.json         # Project dependencies and scripts
```

## Available Scripts

### Development

```bash
npm start
```

Runs both the backend and frontend in development mode with hot reloading. The application will be available at `http://localhost:8005`.

### Backend Only

```bash
npm run backend:development
```

Starts the Express server with nodemon for auto-restart on file changes.

```bash
npm run backend:build
```

Runs the Express server in production mode.

### Frontend Only

```bash
npm run frontend:development
```

Starts the webpack dev server with hot module replacement.

```bash
npm run frontend:build
```

Builds the frontend assets for production with optimizations.

## Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `PRISMIC_ENDPOINT` | Your Prismic repository API endpoint | Yes |
| `PRISMIC_ACCESS_TOKEN` | Prismic access token (if repository is private) | Conditional |
| `PORT` | Server port (default: 8005) | No |

## Development Workflow

1. **Start the development server**

```bash
npm start
```

2. **Access the application**

Open your browser and navigate to `http://localhost:8005`

3. **Make changes**

- Edit Pug templates in the `views/` directory
- Modify styles in the `styles/` directory
- Update JavaScript in the `app/` directory
- Changes will automatically reload in the browser

4. **Build for production**

```bash
npm run frontend:build
npm run backend:build
```

## Prismic CMS Setup

### 1. Create a Prismic Repository

1. Sign up or log in to [Prismic](https://prismic.io)
2. Create a new repository
3. Get your API endpoint and access token

### 2. Define Custom Types

Create these custom types in your Prismic repository:

**Meta (Single)**
- Used for site-wide metadata (title, description, favicon, etc.)

**Home (Single)**
- Gallery field (for homepage images)
- Additional content fields as needed

**About (Single)**
- Gallery field
- Slice zone with "gallery" slice type

**Collection (Repeatable)**
- Title field
- Products field (Content Relationship to Product type)

**Product (Repeatable)**
- Title field
- Image field
- Description field
- Related collection field

### 3. Populate Content

Add content to your Prismic repository matching the custom types you've created.

## WebGL and Animations

This project includes setup for:

- **GSAP** - For smooth page transitions and scroll-based animations
- **OGL** - For WebGL effects and 3D graphics
- **GLSL Shaders** - Supported via glslify-loader

You can extend these capabilities by adding custom animations and WebGL scenes in the `app/` directory.

## Code Quality

The project includes:

- **ESLint** - JavaScript linting with Standard config
- **Prettier** - Code formatting
- **EditorConfig** - Consistent coding styles

Run linting:

```bash
npx eslint .
```

## Troubleshooting

### Common Issues

**1. Prismic API errors**
- Verify your `PRISMIC_ENDPOINT` is correct
- Check if your repository requires an access token
- Ensure your custom types match the API queries in `app.js`

**2. Port already in use**
- Change the `PORT` in your `.env` file
- Kill the process using port 8005: `lsof -ti:8005 | xargs kill`

**3. Module not found errors**
- Delete `node_modules` and `package-lock.json`
- Run `npm install` again

**4. Webpack build errors**
- Clear webpack cache: `rm -rf node_modules/.cache`
- Rebuild: `npm run frontend:build`

## Migration from Prismic v5 to v6

This project uses Prismic v6, which includes breaking changes from v5:

- Uses `@prismicio/client` instead of `prismic-javascript`
- Uses `@prismicio/helpers` instead of `prismic-dom`
- New API client initialization with `createClient()`
- Updated query predicates syntax

If you're migrating from v5, refer to the [Prismic migration guide](https://prismic.io/docs/technical-reference/prismicio-client).

## Performance Optimization

The production build includes:

- JavaScript minification (Terser)
- CSS extraction and minification
- Image optimization (JPEG, PNG, GIF, SVG)
- Code splitting
- Asset caching

## Browser Support

This project supports all modern browsers:

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

WebGL features require WebGL-capable browsers.

## Credits

- Inspired by [Luis Henrique Bizzaro's Awwwards course](https://www.awwwards.com/academy/course/crafting-immersive-creative-websites-from-scratch)
- Created by [whizzbbig](https://github.com/whizzbbig)
- Built for developers struggling with Prismic v5 to v6 migration

## License

ISC

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Support

For issues and questions:
- Check existing [issues](https://github.com/whizzbbig/Webpack-boilerplate/issues)
- Create a new issue with detailed information
- Refer to Prismic documentation for CMS-related questions

---

Happy coding! 🚀
