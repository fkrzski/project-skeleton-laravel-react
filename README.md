<p>
    <a href="https://github.com/fkrzski/project-skeleton-laravel-react/actions"><img src="https://github.com/fkrzski/project-skeleton-laravel-react/actions/workflows/tests.yml/badge.svg" alt="Build Status"></a>
    <a href="https://packagist.org/packages/fkrzski/project-skeleton-laravel-react"><img src="https://img.shields.io/packagist/dt/fkrzski/project-skeleton-laravel-react" alt="Total Downloads"></a>
    <a href="https://packagist.org/packages/fkrzski/project-skeleton-laravel-react"><img src="https://img.shields.io/packagist/v/fkrzski/project-skeleton-laravel-react" alt="Latest Stable Version"></a>
    <a href="https://packagist.org/packages/fkrzski/project-skeleton-laravel-react"><img src="https://img.shields.io/packagist/l/fkrzski/project-skeleton-laravel-react" alt="License"></a>
</p>

**Laravel Starter Kit (Inertia & React)** is an ultra-strict, type-safe [Laravel](https://laravel.com) skeleton engineered for developers who refuse to compromise on code quality. This opinionated starter kit enforces rigorous development standards through meticulous tooling configuration and architectural decisions that prioritize type safety, immutability, and fail-fast principles.

Includes [Laravel Sail](https://laravel.com/docs/sail) for seamless Docker-based development environment, ensuring consistency across all development machines.

## Why This Starter Kit?

Modern PHP has evolved into a mature, type-safe language, yet many Laravel projects still operate with loose conventions and optional typing. This starter kit changes that paradigm by enforcing:

- **Fully Actions-Oriented Architecture**: Every operation is encapsulated in a single-action class
- **Cruddy by Design**: Standardized CRUD operations for all controllers, actions, and Inertia & React pages
- **100% Type Coverage**: Every method, property, and parameter is explicitly typed
- **Zero Tolerance for Code Smells**: Rector, PHPStan, ESLint, and Prettier at maximum strictness catch issues before they become bugs
- **Immutable-First Architecture**: Data structures favor immutability to prevent unexpected mutations
- **Fail-Fast Philosophy**: Errors are caught at compile-time, not runtime
- **Automated Code Quality**: Pre-configured tools ensure consistent, pristine code across your entire team
- **Just Better Laravel Defaults**: Thanks to **[Essentials](https://github.com/nunomaduro/essentials)** / strict models, auto eager loading, immutable dates, and more...
- **AI Guidelines**: Integrated AI Guidelines to assist in maintaining code quality and consistency
- **Full Testing Suite**: More than 150 tests with 100% code coverage using Pest
- 
This isn't just another Laravel boilerplate—it's a statement that PHP applications can and should be built with the same rigor as strongly-typed languages like Rust or TypeScript.

## Getting Started

> **Requires [PHP 8.5+](https://php.net/releases/) and a code coverage driver like [pcov](https://github.com/krakjoe/pcov)** for local development, **OR [Docker](https://www.docker.com/get-started)** for Sail-based development.

Create your type-safe Laravel application using [Composer](https://getcomposer.org):

```bash
composer create-project fkrzski/project-skeleton-laravel-react --prefer-dist example-app
```

### Initial Setup with Laravel Sail (Recommended)

Navigate to your project and start using Docker containers:

```bash
cd example-app

# Install dependencies (if not already installed)
composer install

# Start Sail containers
./vendor/bin/sail up -d

# Run setup inside the container
./vendor/bin/sail composer setup

# Your application is now running at http://localhost
```

**Pro tip:** Create a shell alias for Sail:
```bash
alias sail='./vendor/bin/sail'
```

Then you can use `sail` instead of `./vendor/bin/sail`:
```bash
sail up -d
sail composer setup
sail artisan migrate
```

### Initial Setup (Local Development)

Alternatively, you can run the project locally without Docker:

```bash
cd example-app

# Setup the project
composer setup

# Start the development server
composer dev
```

### Optional: Browser Testing Setup

If you plan to use Pest's browser testing capabilities:

```bash
# Local
npm install playwright
npx playwright install

# With Sail
./vendor/bin/sail npm install playwright
./vendor/bin/sail npx playwright install
```

### Verify Installation

Run the test suite to ensure everything is configured correctly:

```bash
# Local
composer test

# With Sail
./vendor/bin/sail composer test
```

You should see 100% test coverage and all quality checks passing.

## Available Tooling

> **Note:** All commands below can be prefixed with `./vendor/bin/sail` when using Laravel Sail (e.g., `./vendor/bin/sail composer test`)

### Setup & Development
- `composer setup` - Complete project setup (install dependencies, generate key, run migrations, build assets)
- `composer dev` - Starts Laravel server, queue worker, log monitoring, and Vite dev server concurrently

### Code Quality
- `composer pint` - Runs Laravel Pint (PHP code formatter) on modified files
- `composer analyse` - Runs PHPStan static analysis
- `composer refactor` - Runs Rector for automated refactoring
- `composer lint` - Runs all formatters: Rector, Pint, and Prettier (JS/TS/CSS)

### Testing - Unit & Coverage
- `composer test:unit` - Runs Pest tests in parallel with code coverage
- `composer test:unit:mutation` - Runs mutation testing with minimum 100% score
- `composer test:type-coverage` - Ensures 100% type coverage with Pest
- `composer test:profanity` - Checks for profanity in test names

### Testing - Static Analysis
- `composer test:env` - Validates required environment variables
- `composer test:syntax` - Checks PHP syntax in all files
- `composer test:types` - Runs PHPStan and TypeScript type checking
- `composer test:lint` - Dry-run mode for linters (CI/CD pipelines)
- `composer test:pint` - Pint in test mode (doesn't modify files)
- `composer test:refactor` - Rector in dry-run mode

### Testing - Complete Suite
- `composer test` - Runs the complete test suite:
  - Environment validation
  - Profanity check
  - Syntax validation
  - All linters (dry-run)
  - Type checking (PHPStan + TypeScript)
  - Type coverage (100% minimum)
  - Unit tests (parallel with coverage)
  - Mutation testing (100% minimum)

### Maintenance
- `composer update:requirements` - Updates all PHP and NPM dependencies to latest versions

## License

**Laravel Starter Kit Inertia React** was created by **[Filip Krzyżanowski](https://www.linkedin.com/in/fkrzski/)** under the **[MIT license](https://opensource.org/licenses/MIT)**.
