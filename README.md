# Awesome Laravel

> A curated list of Laravel 13.x features, official packages, community packages, observability tooling, self-hosted infra patterns, YouTube channels, and websites. Inspired by [awesome-php](https://github.com/ziadoz/awesome-php) and other awesome lists.

Maintained under [sudo-su-coffee](https://github.com/sudo-su-coffee). Contributions welcome — see [CONTRIBUTING.md](CONTRIBUTING.md).

## YouTube Channels

| Channel | Focus |
|---|---|
| [Laravel](https://www.youtube.com/@LaravelPHP) | Official channel — conference talks, feature announcements |
| [Laravel Daily](https://www.youtube.com/@LaravelDaily) | Tutorials, package roundups, real-world patterns |
| [Grant Harting](https://www.youtube.com/@grant_harting) | In-depth Laravel/PHP tutorials |
| [CodeHead](https://www.youtube.com/@codehead01) | Laravel tutorials and project walkthroughs |

## Websites

| Site | What it is |
|---|---|
| [Laravel News](https://laravel-news.com) | News, package releases, tutorials |
| [Laravel Daily (site)](https://laraveldaily.com) | Tutorials + [packages directory](https://laraveldaily.com/packages) |
| [Laracasts](https://laracasts.com) | Official-adjacent video courses (Jeffrey Way) |
| [Spatie Open Source](https://spatie.be/open-source/packages) | Full catalog from Laravel's most prolific package maintainer |
| [Packagist](https://packagist.org) | Official PHP package registry |
| [Packalyst](http://packalyst.com) | Laravel-specific package directory |
| [Laravel.com](https://laravel.com) | Official site & [docs](https://laravel.com/docs) |
| [awesome-laravel (chiraggude)](https://github.com/chiraggude/awesome-laravel) | Curated list: essentials, hosting, deployment, learning resources |
| [Best-Laravel-Packages (LaravelDaily)](https://github.com/LaravelDaily/Best-Laravel-Packages) | Curated package list on GitHub |

## Contents

- [Laravel Version History (8 → 13)](#laravel-version-history-8--13)
- [Laravel 13 Highlights](#laravel-13-highlights)
- [First-Party Packages](#first-party-packages)
- [Admin Panels / CRUD](#admin-panels--crud)
- [Auth, Permissions, Multi-tenancy](#auth-permissions-multi-tenancy)
- [Data, DTOs, Query Building](#data-dtos-query-building)
- [Media, Files, Uploads](#media-files-uploads)
- [Excel / Import-Export / PDF](#excel--import-export--pdf)
- [API Development](#api-development)
- [Search](#search)
- [Testing](#testing)
- [Settings, Config, Feature Flags](#settings-config-feature-flags)
- [Activity Logging, Auditing](#activity-logging-auditing)
- [Backups, Health, Monitoring](#backups-health-monitoring)
- [Localization / Translation](#localization--translation)
- [Queues, Jobs, Scheduling](#queues-jobs-scheduling)
- [Payments / Billing](#payments--billing)
- [E-Commerce Platforms / Packages](#e-commerce-platforms--packages)
- [Gig / Delivery Platform Building Blocks](#gig--delivery-platform-building-blocks)
- [Kafka](#kafka)
- [Code Quality / Static Analysis](#code-quality--static-analysis)
- [Dev Environment / Tooling](#dev-environment--tooling)
- [Debugging Tools](#debugging-tools)
- [Octane — Performance](#octane--performance)
- [HTTP, Utilities, Misc](#http-utilities-misc)
- [Livewire / Frontend Companions](#livewire--frontend-companions)
- [AI / Vector / Embeddings](#ai--vector--embeddings)
- [Observability — Metrics, Tracing, Errors](#observability--metrics-tracing-errors)
- [Database Infra](#database-infra)
- [Backup Storage](#backup-storage)
- [API Testing Tools](#api-testing-tools)
- [Log Aggregation](#log-aggregation)

---

## Laravel Version History (8 → 13)

| # | Released | PHP req. | Key new features |
|---|---|---|---|
| **8** | Sep 8, 2020 | 7.3+ | Laravel Jetstream, `app/Models` directory, class-based model factories, migration squashing (`schema:dump`), improved rate limiting, time testing helpers (`Carbon` time travel), dynamic Blade components, job batching (`Bus::batch()`), maintenance mode with pre-rendered view |
| **9** | Feb 8, 2022 | 8.0+ | Symfony 6.0 components, Symfony Mailer (replaced SwiftMailer), Flysystem 3.0, Scout database driver, new accessor/mutator syntax (`Attribute::make()`), implicit route bindings via Enums, controller route grouping, `route:list` improvements, forced scoped bindings, Laravel moved to annual release cycle starting here |
| **10** | Feb 14, 2023 | 8.1+ | Process facade (`Process::run()`, concurrent pools, faking), invokable validation rules by default, native PHP type declarations across skeleton code, **Laravel Pennant** (feature flags) introduced, `Str::password()`, test profiling (`--profile`), Horizon/Telescope UI refresh |
| **11** | Mar 12, 2024 | 8.2+ | Slimmed-down default app skeleton (single `AppServiceProvider`, no default middleware files), per-second rate limiting, health check routing (`/up`), **Laravel Reverb** (WebSocket server) introduced, `Prompts` for CLI, graceful encryption key rotation, `once()` helper, Dumpable trait, resendable email verification |
| **12** | Feb 24, 2025 | 8.2–8.5 | New official starter kits (React/Svelte/Vue/Livewire on Inertia 2 + TypeScript + shadcn/ui / Flux+Volt), WorkOS AuthKit variant per kit, Breeze/Jetstream deprecated, Carbon 3-only, JSON cast Unicode preservation, minimal-breaking "maintenance release" |
| **13** | Mar 17, 2026 | 8.3–8.5 | **Laravel AI SDK** (text/tools/embeddings/audio/images), native JSON:API resources, `PreventRequestForgery` CSRF middleware, queue routing by class (`Queue::route()`), expanded PHP attributes (`#[Middleware]`, `#[Authorize]`, `#[Tries]`, `#[Backoff]`, `#[Timeout]`, `#[FailOnTimeout]`), `Cache::touch()`, native vector/semantic search (`whereVectorSimilarTo()` + pgvector) |

Official release notes: [8.x](https://laravel.com/docs/8.x/releases) · [9.x](https://laravel.com/docs/9.x/releases) · [10.x](https://laravel.com/docs/10.x/releases) · [11.x](https://laravel.com/docs/11.x/releases) · [12.x](https://laravel.com/docs/12.x/releases) · [13.x](https://laravel.com/docs/13.x/releases)

## Laravel 13 Highlights

Laravel 13.0 — March 17, 2026. Requires PHP 8.3+. [Official release notes](https://laravel.com/framework/docs/13.x/releases).

- **Laravel AI SDK** — first-party, unified API for text generation, tool-calling agents, embeddings, audio, images, vector-store integration.
- **JSON:API Resources** — native JSON:API-compliant resource serialization.
- **`PreventRequestForgery`** — formalized, origin-aware CSRF middleware.
- **Queue routing by class** — `Queue::route(Job::class, connection: 'redis', queue: 'name')`.
- **Expanded PHP attributes** — `#[Middleware]`, `#[Authorize]`, `#[Tries]`, `#[Backoff]`, `#[Timeout]`, `#[FailOnTimeout]`.
- **`Cache::touch()`** — extend TTL without re-storing value.
- **Native semantic/vector search** — `whereVectorSimilarTo()` against PostgreSQL + `pgvector`.

Carried over from Laravel 12: React/Svelte/Vue/Livewire starter kits (Inertia 2, TypeScript, shadcn/ui / Flux UI + Volt), WorkOS AuthKit variant per kit, Carbon 3-only.

## First-Party Packages

| Package | Purpose |
|---|---|
| [Sanctum](https://laravel.com/docs/sanctum) | Lightweight SPA/mobile token auth |
| [Passport](https://laravel.com/docs/passport) | Full OAuth2 server |
| [Socialite](https://laravel.com/docs/socialite) | OAuth login (Google, GitHub, etc.) |
| [Horizon](https://laravel.com/docs/horizon) | Redis queue dashboard/monitoring |
| [Octane](https://laravel.com/docs/octane) | High-performance app server (FrankenPHP/Swoole/RoadRunner) |
| [Reverb](https://laravel.com/docs/reverb) | First-party WebSocket server |
| [Echo](https://laravel.com/docs/broadcasting) | JS client for broadcasting/WebSockets |
| [Scout](https://laravel.com/docs/scout) | Full-text search driver abstraction |
| [Pennant](https://laravel.com/docs/pennant) | Feature flags |
| [Pulse](https://laravel.com/docs/pulse) | Real-time app performance monitoring dashboard |
| [Nightwatch](https://nightwatch.laravel.com) | APM/observability product (paid) |
| [Telescope](https://laravel.com/docs/telescope) | Local debugging/request inspector |
| [Dusk](https://laravel.com/docs/dusk) | Browser testing (Selenium-based) |
| [Cashier](https://laravel.com/docs/billing) | Stripe/Paddle billing/subscriptions |
| [Pint](https://laravel.com/docs/pint) | Opinionated PHP code style fixer |
| [Sail](https://laravel.com/docs/sail) | Docker dev environment |
| [Valet](https://laravel.com/docs/valet) | macOS local dev environment |
| [Forge](https://forge.laravel.com) / [Vapor](https://vapor.laravel.com) / [Cloud](https://laravel.com/cloud) | Hosting/deployment (paid) |
| [Nova](https://nova.laravel.com) | Admin panel (paid) |

## Admin Panels / CRUD

| Package | Purpose |
|---|---|
| [filamentphp/filament](https://github.com/filamentphp/filament) | TALL-stack admin panel builder — current dominant choice |
| [laravel/nova](https://nova.laravel.com) | Official paid admin panel |
| [orchid/platform](https://github.com/orchidsoftware/platform) | Alternative admin panel framework |
| [backpack/crud](https://github.com/Laravel-Backpack/CRUD) | CRUD generator + admin panel |
| [voyager/voyager](https://github.com/the-control-group/voyager) | Older BREAD-based admin panel (lightly maintained) |

## Auth, Permissions, Multi-tenancy

| Package | Purpose |
|---|---|
| [spatie/laravel-permission](https://github.com/spatie/laravel-permission) | Roles & permissions — near-universal standard |
| [laravel/fortify](https://github.com/laravel/fortify) | Headless auth backend |
| [laravel/jetstream](https://github.com/laravel/jetstream) | Auth scaffolding (deprecated in favor of new starter kits) |
| [tymon/jwt-auth](https://github.com/tymondesigns/jwt-auth) | JWT authentication |
| [stancl/tenancy](https://github.com/archtechx/tenancy) | Most mature multi-tenancy package |
| [spatie/laravel-multitenancy](https://github.com/spatie/laravel-multitenancy) | Alternative multi-tenancy |
| [lab404/laravel-impersonate](https://github.com/404labfr/laravel-impersonate) | User impersonation for support/admin |
| [workos/workos-php](https://github.com/workos/workos-php) | WorkOS AuthKit integration (SSO/passkeys) |

## Data, DTOs, Query Building

| Package | Purpose |
|---|---|
| [spatie/laravel-data](https://github.com/spatie/laravel-data) | Typed DTOs with validation/transformation |
| [spatie/laravel-query-builder](https://github.com/spatie/laravel-query-builder) | Build API filters/sorts from query params |
| [spatie/laravel-fractal](https://github.com/spatie/laravel-fractal) | API response transformation |
| [league/fractal](https://github.com/thephpleague/fractal) | Underlying transformer library |
| [spatie/laravel-model-states](https://github.com/spatie/laravel-model-states) | State machine pattern on models |
| [spatie/laravel-model-status](https://github.com/spatie/laravel-model-status) | Track status history on models |
| [spatie/enum](https://github.com/spatie/enum) | Enum helper library |
| [bensampo/laravel-enum](https://github.com/BenSampo/laravel-enum) | Alternative enum implementation |

## Media, Files, Uploads

| Package | Purpose |
|---|---|
| [spatie/laravel-medialibrary](https://github.com/spatie/laravel-medialibrary) | File/media attachment management — standard choice |
| [spatie/laravel-image-optimizer](https://github.com/spatie/laravel-image-optimizer) | Auto-optimize uploaded images |
| [intervention/image](https://github.com/Intervention/image) | Image manipulation library |
| [league/flysystem-aws-s3-v3](https://github.com/thephpleague/flysystem-aws-s3-v3) | S3 (and S3-compatible) filesystem driver |
| [spatie/laravel-glide](https://github.com/spatie/laravel-glide) | On-the-fly image manipulation via URL |

## Excel / Import-Export / PDF

| Package | Purpose |
|---|---|
| [maatwebsite/excel](https://github.com/SpartnerNL/Laravel-Excel) | Excel import/export — standard |
| [barryvdh/laravel-dompdf](https://github.com/barryvdh/laravel-dompdf) | PDF generation (HTML to PDF) |
| [barryvdh/laravel-snappy](https://github.com/barryvdh/laravel-snappy) | PDF/image generation via wkhtmltopdf |
| [spatie/laravel-pdf](https://github.com/spatie/laravel-pdf) | Modern PDF generation via headless Chrome |
| [spatie/browsershot](https://github.com/spatie/browsershot) | Screenshot/PDF via Puppeteer/Chrome |

## API Development

| Package | Purpose |
|---|---|
| [dedoc/scramble](https://github.com/dedoc/scramble) | Auto-generate OpenAPI docs from code, no annotations |
| [darkaonline/l5-swagger](https://github.com/DarkaOnLine/L5-Swagger) | Swagger/OpenAPI docs via annotations |
| [spatie/laravel-json-api-paginate](https://github.com/spatie/laravel-json-api-paginate) | JSON:API-style pagination |

## Search

| Package | Purpose |
|---|---|
| [laravel/scout](https://laravel.com/docs/scout) | Search driver abstraction (first-party) |
| [meilisearch/meilisearch-php](https://github.com/meilisearch/meilisearch-php) | Self-hostable search engine driver |
| [typesense/typesense-php](https://github.com/typesense/typesense-php) | Alternative self-hostable search driver |
| [algolia/scout-extended](https://github.com/algolia/scout-extended) | Algolia-specific Scout extensions (SaaS) |

## Testing

| Package | Purpose |
|---|---|
| [pestphp/pest](https://github.com/pestphp/pest) | Modern testing framework — default preference over raw PHPUnit |
| [pestphp/pest-plugin-laravel](https://github.com/pestphp/pest-plugin-laravel) | Laravel-specific Pest helpers |
| [laravel/dusk](https://laravel.com/docs/dusk) | Browser testing (first-party) |
| [mockery/mockery](https://github.com/mockery/mockery) | Mocking library |
| [fakerphp/faker](https://github.com/FakerPHP/Faker) | Fake data generation |
| [spatie/pest-plugin-snapshots](https://github.com/spatie/pest-plugin-snapshots) | Snapshot testing for Pest |
| [nunomaduro/collision](https://github.com/nunomaduro/collision) | Better CLI error output for tests |

## Settings, Config, Feature Flags

| Package | Purpose |
|---|---|
| [spatie/laravel-settings](https://github.com/spatie/laravel-settings) | Typed app settings stored in DB |
| [laravel/pennant](https://laravel.com/docs/pennant) | Feature flags (first-party) |
| [spatie/laravel-feature-flags](https://github.com/spatie/laravel-feature-flags) | Alternative feature flag package |

## Activity Logging, Auditing

| Package | Purpose |
|---|---|
| [spatie/laravel-activitylog](https://github.com/spatie/laravel-activitylog) | Model change tracking — standard |
| [owen-it/laravel-auditing](https://github.com/owen-it/laravel-auditing) | Alternative audit trail package |

## Backups, Health, Monitoring

| Package | Purpose |
|---|---|
| [spatie/laravel-backup](https://github.com/spatie/laravel-backup) | DB + file backups to S3/etc. |
| [spatie/laravel-health](https://github.com/spatie/laravel-health) | Application health check dashboard |
| [laravel/pulse](https://laravel.com/docs/pulse) | Real-time app performance monitoring (first-party) |
| [sentry/sentry-laravel](https://github.com/getsentry/sentry-laravel) | Error tracking/monitoring |
| [bugsnag/bugsnag-laravel](https://github.com/bugsnag/bugsnag-laravel) | Alternative error tracking |

## Localization / Translation

| Package | Purpose |
|---|---|
| [spatie/laravel-translatable](https://github.com/spatie/laravel-translatable) | Translatable model attributes |
| [mcamara/laravel-localization](https://github.com/mcamara/laravel-localization) | URL/route localization |
| [spatie/laravel-translation-loader](https://github.com/spatie/laravel-translation-loader) | DB-backed translation strings |

## Queues, Jobs, Scheduling

| Package | Purpose |
|---|---|
| [laravel/horizon](https://laravel.com/docs/horizon) | Redis queue dashboard/monitoring (first-party) |
| [spatie/laravel-queueable-action](https://github.com/spatie/laravel-queueable-action) | Single-purpose action classes as jobs |
| [spatie/laravel-schedule-monitor](https://github.com/spatie/laravel-schedule-monitor) | Monitor scheduled task execution/failures |
| [laravel/reverb](https://laravel.com/docs/reverb) | Self-hosted WebSocket server (first-party) |

## Payments / Billing

| Package | Purpose |
|---|---|
| [laravel/cashier](https://laravel.com/docs/billing) | Stripe billing/subscriptions (first-party) |
| [laravel/cashier-paddle](https://github.com/laravel/cashier-paddle) | Paddle billing variant (first-party) |
| [srmklive/paypal](https://github.com/srmklive/laravel-paypal) | PayPal integration |

### Indian Payment Gateways
| Package | Gateways covered | Notes |
|---|---|---|
| [anandsiddharth/laravel-razorpay](https://github.com/anandsiddharth/laravel-razorpay) | Razorpay | Thin wrapper around Razorpay's official PHP SDK — most common Razorpay integration path |
| [razorpay/razorpay](https://github.com/razorpay/razorpay-php) | Razorpay | Official SDK (framework-agnostic), use directly if you don't want a wrapper |
| [rushabhmishrarmz/indipay](https://github.com/rushabhmishrarmz/indipay) | CCAvenue, PayUMoney, EBS, CitrusPay, InstaMojo, Mobikwik/ZapakPay, Paytm | Actively maintained fork of the older `softon/indipay`/`ineffablesam/indipay-2` lineage — targets Laravel 10+ |
| [PayU India](https://docs.payu.in) | PayU | No strongly-maintained Laravel wrapper as of writing — most teams call PayU's REST API directly via Guzzle/Http facade |
| [PhonePe](https://developer.phonepe.com) | PhonePe | No mainstream Laravel package — integrate via their REST API directly |

**Reality check**: the "Indian payment gateway" Laravel package space is fragmented and thinly maintained — `indipay` has had several forks/rewrites over the years (nickatwork → dbhosale → softon → ineffablesam → rushabhmishrarmz), each essentially the same wrapper. For anything beyond Razorpay (which has solid first-party SDK support), calling the gateway's REST API directly via Laravel's `Http` facade is often more reliable than trusting an unmaintained wrapper — worth weighing per-project rather than defaulting to a package.

## E-Commerce Platforms / Packages

| Package | Type | Notes |
|---|---|---|
| [aimeos/aimeos-laravel](https://github.com/aimeos/aimeos-laravel) | Full e-commerce package (not standalone app) | API-first, cloud-native, 130k+ installs, handles B2B/marketplace scale, actively maintained |
| [bagisto/bagisto](https://github.com/bagisto/bagisto) | Standalone e-commerce application (Laravel + Vue) | Full store out of the box, good RTL/Middle-East support, has an [Octane plugin](https://packagist.org/packages/winter/wn-octane-plugin) |
| [lunarphp/lunar](https://github.com/lunarphp/lunar) | Headless e-commerce package | API-first, modern, good for custom storefronts |
| [vanilophp/framework](https://github.com/vanilophp/framework) | Modular e-commerce package | Pick-and-choose modules (cart, checkout, etc.) rather than a monolith |
| [getcandy/getcandy](https://github.com/getcandy/getcandy) | Headless e-commerce package | Filament-based admin, API-first |

**Pick guide**: full standalone app → Bagisto. Add e-commerce to an existing Laravel app → Aimeos or Lunar. Fully custom/composable → Vanilo.

## Gig / Delivery Platform Building Blocks

Laravel's package ecosystem for real-time dispatch/geolocation is genuinely thin — most production gig/delivery platforms (including your own dispatchd-go work) end up hand-rolling geospatial indexing rather than relying on these. Listed for completeness:

| Package | Purpose | Notes |
|---|---|---|
| [netsells/laravel-geoscope](https://github.com/netsells/laravel-geoscope) | Distance queries + geofencing via model trait/query builder | Uses native DB functions (not haversine in PHP) — MySQL/MariaDB/Postgres/SQL Server. Best-maintained option in this category. |
| [salmanzafar/laravel-geo-fence](https://packagist.org/packages/salmanzafar/laravel-geo-fence) | Simple lat/long distance calculator | Basic haversine wrapper, fine for low-volume use |
| PostGIS (Postgres extension, not Composer) | Proper geospatial indexing/queries | If you're outgrowing haversine-in-PHP packages, this — plus raw queries — is the actual scalable path, same category of decision you already made going custom with sharded geohash in Go |
| [laravel/reverb](https://laravel.com/docs/reverb) | Real-time rider/order location broadcasting | Self-hosted WebSocket layer for live tracking UI |
| [spatie/laravel-model-states](https://github.com/spatie/laravel-model-states) | Order/trip state machine | Relevant to the trip/order state machine you still need for the gig platform |
| [mateusjunges/laravel-kafka](https://laravelkafka.com) | Kafka producer/consumer for Laravel | See Kafka section below — relevant for event-driven order/dispatch pipelines at scale |

**Honest take**: for anything beyond basic radius queries, Laravel packages won't get you where dispatchd-go already is (sharded geohash + Vyukov MPMC). These are useful for a Laravel-side admin/reporting layer talking to Postgres, not for replacing your matching engine.

## Kafka

| Package | Notes |
|---|---|
| [mateusjunges/laravel-kafka](https://laravelkafka.com) | **Standard choice** — 4M+ downloads, 728+ stars, actively maintained, dedicated docs site. Chainable producer API, consumer builder with groups/handlers, invokable handler classes, JSON serialization built-in. Requires PHP `ext-rdkafka`. Laravel 9+. |
| `ext-rdkafka` (PECL, not Composer) | Required PHP extension — `pecl install rdkafka`, needs `librdkafka` system library installed first |
| [junges/kafka batch fork (chocofamilyme/laravel-kafka)](https://github.com/vevovip/laravel-kafka) | Adds batch produce/consume on top of `mateusjunges/laravel-kafka` — useful if you're doing high-throughput event batches |

**Setup note**: `librdkafka` (system lib) → `pecl install rdkafka` (PHP ext) → `composer require mateusjunges/laravel-kafka`, in that order. Most install failures come from skipping the system library step.

## Code Quality / Static Analysis

| Package | Purpose |
|---|---|
| [laravel/pint](https://laravel.com/docs/pint) | Opinionated code style fixer (first-party) |
| [phpstan/phpstan](https://github.com/phpstan/phpstan) | Static analysis |
| [larastan/larastan](https://github.com/larastan/larastan) | PHPStan rules tailored for Laravel/Eloquent |
| [rector/rector](https://github.com/rectorphp/rector) | Automated refactoring/upgrades |
| [nunomaduro/phpinsights](https://github.com/nunomaduro/phpinsights) | Code quality scoring |

## Dev Environment / Tooling

| Package | Purpose |
|---|---|
| [laravel/sail](https://laravel.com/docs/sail) | Docker dev environment (first-party) |
| [laravel/valet](https://laravel.com/docs/valet) | macOS local dev environment (first-party) |
| [laravel/tinker](https://github.com/laravel/tinker) | REPL (first-party, ships by default) |
| [beyondcode/laravel-dump-server](https://github.com/beyondcode/laravel-dump-server) | Standalone dump server |

## Debugging Tools

| Package | Approach | Notes |
|---|---|---|
| [barryvdh/laravel-debugbar](https://github.com/barryvdh/laravel-debugbar) | In-page toolbar | v4 released Jan 2026 (major rewrite). 20M+ downloads. Dev-only — never enable in production. |
| [itsgoingd/clockwork](https://github.com/itsgoingd/clockwork) | Browser extension panel, no HTML injection | Lighter than Debugbar; better for API-only apps/SPAs. |
| [spatie/ray](https://github.com/spatie/laravel-ray) | Sends output to separate desktop app | Paid desktop app; good for multi-project debugging. |
| [laravel/telescope](https://laravel.com/docs/telescope) | Full first-party dashboard (DB-backed) | Deeper introspection: exceptions, jobs, notifications, scheduled tasks. |
| [laravel/nightwatch](https://nightwatch.laravel.com) | Production APM (paid) | Positioned to replace Datadog/New Relic for Laravel-specific needs. |
| [spatie/laravel-ignition](https://github.com/spatie/laravel-ignition) | Enhanced error page | Default in new installs; one-click fixes for common errors. |

## Octane — Performance

Keeps the app booted in memory across requests instead of bootstrapping per-request (PHP-FPM model).

| Server | When to use |
|---|---|
| **FrankenPHP** | Default recommendation (2026). Go-based, bundles web server (Caddy) + TLS. Early hints, Brotli/Zstandard, auto HTTPS. |
| **RoadRunner** | Mature, process-isolated monolith deployments. |
| **Swoole / Open Swoole** | Only if you need coroutines, concurrent tasks, ticks, or Octane's in-memory cache/tables. |

```bash
composer require laravel/octane
php artisan octane:install --server=frankenphp
php artisan octane:start
```

**Gotcha**: static properties, singletons, and closure-captured objects persist across requests — set `max-requests`/`max-jobs` recycle limits, register listeners only in service providers, never mutate static arrays in handlers.

| Package | Purpose |
|---|---|
| [laravel/octane](https://github.com/laravel/octane) | Core package |
| [spiral/roadrunner-http](https://github.com/spiral/roadrunner-http), spiral/roadrunner-cli | Required extras for RoadRunner |

## HTTP, Utilities, Misc

| Package | Purpose |
|---|---|
| [spatie/laravel-sluggable](https://github.com/spatie/laravel-sluggable) | Auto-generate slugs on models |
| [spatie/laravel-sitemap](https://github.com/spatie/laravel-sitemap) | XML sitemap generation |
| [spatie/laravel-tags](https://github.com/spatie/laravel-tags) | Taggable models |
| [spatie/laravel-comments](https://github.com/spatie/laravel-comments) | Commenting system for models |
| [spatie/laravel-webhook-client](https://github.com/spatie/laravel-webhook-client) | Receive & verify incoming webhooks |
| [spatie/laravel-webhook-server](https://github.com/spatie/laravel-webhook-server) | Send webhooks with retries |
| [spatie/laravel-csp](https://github.com/spatie/laravel-csp) | Content Security Policy header management |
| [spatie/laravel-cookie-consent](https://github.com/spatie/laravel-cookie-consent) | GDPR cookie consent banner |
| [spatie/laravel-honeypot](https://github.com/spatie/laravel-honeypot) | Spam form protection |
| [spatie/laravel-login-link](https://github.com/spatie/laravel-login-link) | Passwordless magic-link login |
| [spatie/laravel-url-signer](https://github.com/spatie/laravel-url-signer) | Signed URL generation/verification |
| [spatie/laravel-collection-macros](https://github.com/spatie/laravel-collection-macros) | Extra Collection helper methods |
| [laravel-notification-channels](https://github.com/laravel-notification-channels) (org) | Extra notification channels (Telegram, Slack, Discord, WhatsApp, etc.) |
| [guzzlehttp/guzzle](https://github.com/guzzle/guzzle) | HTTP client (Laravel's `Http` facade wraps this) |
| [doctrine/dbal](https://github.com/doctrine/dbal) | Required for certain migration column-modification operations |
| [predis/predis](https://github.com/predis/predis) | Redis client (pure PHP, no ext required) |
| [phpoffice/phpspreadsheet](https://github.com/PHPOffice/PhpSpreadsheet) | Underlying library for maatwebsite/excel |

## Livewire / Frontend Companions

| Package | Purpose |
|---|---|
| [livewire/livewire](https://github.com/livewire/livewire) | Full-stack reactive components without leaving Blade |
| [livewire/volt](https://github.com/livewire/volt) | Functional/single-file Livewire component syntax |
| [livewire/flux](https://fluxui.dev) | Official Livewire UI component library (used in 12.x/13.x starter kits) |
| [wire-elements/modal](https://github.com/wire-elements/modal) | Modal component system for Livewire |
| [inertiajs/inertia-laravel](https://github.com/inertiajs/inertia-laravel) | Inertia.js server adapter (React/Vue/Svelte, no separate API layer) |

## AI / Vector / Embeddings

| Package | Purpose |
|---|---|
| [laravel/ai](https://laravel.com/ai) | First-party AI SDK (13.x) — text, tools, embeddings, images, audio |
| [pgvector/pgvector-php](https://github.com/pgvector/pgvector-php) | PHP client for PostgreSQL `pgvector` extension |
| [openai-php/laravel](https://github.com/openai-php/laravel) | OpenAI API wrapper for Laravel (community) |

## Observability — Metrics, Tracing, Errors

### Prometheus
| Package | Notes |
|---|---|
| [lkaemmerling/laravel-horizon-prometheus-exporter](https://github.com/lkaemmerling/laravel-horizon-prometheus-exporter) | Horizon queue metrics for Prometheus — actively maintained |
| [saschahemleb/laravel-prometheus-exporter](https://github.com/saschahemleb/laravel-prometheus-exporter) | General-purpose wrapper around `promphp/prometheus_client_php` |
| [aduzenko/laravel-configurable-prometheus](https://packagist.org/packages/aduzenko/laravel-configurable-prometheus) | Config-driven metric definitions, targets Laravel 12/13 |
| [promphp/prometheus_client_php](https://github.com/promphp/prometheus_client_php) | Underlying PHP Prometheus client |

Use **Redis** as the storage adapter for multi-worker/k8s deploys — in-memory and APCu don't share state across workers.

### OpenTelemetry
| Package | Notes |
|---|---|
| [keepsuit/laravel-opentelemetry](https://github.com/keepsuit/laravel-opentelemetry) | Current best choice — 500k+ installs, active, Laravel 11/12/13. Auto-instruments HTTP, DB, queues, Redis, cache, events, Livewire, Scout. Explicit Octane worker-mode support. |
| [open-telemetry/opentelemetry-auto-laravel](https://github.com/open-telemetry/opentelemetry-php-instrumentation) | Official OTel PHP auto-instrumentation (more manual setup) |

> `overtrue/laravel-open-telemetry` is deprecated — points to `keepsuit/laravel-opentelemetry`.

For Octane: set `OTEL_*` env vars at process/container level, not just `.env`.

### Error Tracking
| Package | Notes |
|---|---|
| [sentry/sentry-laravel](https://github.com/getsentry/sentry-laravel) | Official first-party integration — exceptions, performance traces, breadcrumbs |

## Database Infra

**PgBouncer** (not a Composer package — sits in front of Postgres):
- Point Laravel's `pgsql` connection at PgBouncer's host/port.
- Use session pooling mode if relying on prepared statements, advisory locks, or `SET` commands — transaction pooling breaks these.

## Backup Storage

| Package | Notes |
|---|---|
| [spatie/laravel-backup](https://github.com/spatie/laravel-backup) | DB dump + file backup, health-check notifications |
| [league/flysystem-aws-s3-v3](https://github.com/thephpleague/flysystem-aws-s3-v3) | S3-compatible driver — works against MinIO, Garage, Backblaze B2 too |

## API Testing Tools

| Tool | Notes |
|---|---|
| [pestphp/pest-plugin-laravel](https://github.com/pestphp/pest-plugin-laravel) | HTTP test helpers in Pest syntax |
| [Bruno](https://www.usebruno.com) | FOSS, self-hostable API client (Postman alternative) |
| [Hoppscotch](https://hoppscotch.io) | FOSS, self-hostable API client |

## Log Aggregation

| Tool | Notes |
|---|---|
| [monolog/monolog](https://github.com/Seldaek/monolog) | Underlying logger Laravel ships with |
| Loki + Promtail | Self-hosted log aggregation, pairs with Prometheus/Grafana |
| [arcanedev/log-viewer](https://github.com/ARCANEDEV/LogViewer) | Simple in-app log viewer |

---

## Job Queue Monitoring & Admin Visibility (Horizon vs Telescope vs Others)

**Direct answer to "can I see queue/job reduction in Telescope?"**: partially, not really for production monitoring.

| Tool | What it shows | Fit for job/queue visibility |
|---|---|---|
| [laravel/horizon](https://laravel.com/docs/horizon) | **Purpose-built** for Redis queues — live dashboard of jobs (pending/processing/completed/failed), throughput graphs, wait-time metrics, per-queue breakdown, failed job retry UI, tags for filtering by job type | **This is the right tool for queue monitoring at scale.** Use this, not Telescope, for production job visibility. |
| [laravel/telescope](https://laravel.com/docs/telescope) | Records individual job dispatches/executions as part of general request/event debugging — good for "did this one job run and what did it do" | Not built for live throughput/backlog monitoring — it's a debug log, not an operations dashboard. Fine for dev, wrong tool for watching queue depth in prod. |
| [laravel/pulse](https://laravel.com/docs/pulse) | App-wide performance dashboard — slow jobs, slow queries, exceptions, usage by user, queue sizes as one panel among several | Good complementary high-level view; pairs with Horizon rather than replacing it |
| [spatie/laravel-schedule-monitor](https://github.com/spatie/laravel-schedule-monitor) | Monitors **scheduled tasks** (cron), not queued jobs — alerts if a scheduled command didn't run | Different problem: use alongside Horizon, not instead of it |
| Prometheus + Grafana (via `lkaemmerling/laravel-horizon-prometheus-exporter`) | Exports Horizon's own metrics for long-term retention/alerting (Horizon's UI itself doesn't retain history well) | Add this once Horizon's built-in UI isn't enough for historical trend/alerting needs |

**For your setup**: Horizon as the primary queue dashboard (real-time, per-queue), Pulse for overall app health at a glance, Prometheus+Grafana exporter once you need alerting/history beyond what Horizon's UI retains. Telescope stays for local dev debugging only — don't rely on it in production at this scale (it writes every entry to DB and will itself become a bottleneck under 500k req/sec).

## University Multi-Module Platform Stack (Hostel/Transport/Halls + Full SIS)

Given the actual shape of the project — five Laravel projects: a combined booking system (hostel + transport + hall booking) and a separate full SIS (admissions → course catalog → marks → attendance) — here's what maps to each module.

### Booking System (Hostel / Transport / Hall)
| Package | Purpose |
|---|---|
| [spatie/laravel-model-states](https://github.com/spatie/laravel-model-states) | Booking state machine (requested → confirmed → checked-in → completed → cancelled) |
| [netsells/laravel-geoscope](https://github.com/netsells/laravel-geoscope) | Distance/geofence queries for transport routing (nearest stop, route matching) |
| [spatie/laravel-google-calendar](https://github.com/spatie/laravel-google-calendar) | If hall/room bookings need calendar sync for staff |
| Custom double-booking prevention: DB-level unique constraints + pessimistic locking (`lockForUpdate()`) | Not a package — at this scale, race conditions on hostel room/hall slot booking need row-level locks, not application-level checks. This is the actual hard problem in a booking system, not a package gap. |
| [spatie/laravel-sluggable](https://github.com/spatie/laravel-sluggable) | Clean URLs for hall/room listings |
| [laravel/reverb](https://laravel.com/docs/reverb) | Live seat/room availability updates without polling |
| [spatie/laravel-webhook-client](https://github.com/spatie/laravel-webhook-client) / [webhook-server](https://github.com/spatie/laravel-webhook-server) | If transport booking integrates with an external fleet/GPS provider |

### Student Information System (Admissions → Catalog → Courses → Marks → Attendance)
| Package | Purpose |
|---|---|
| [spatie/laravel-permission](https://github.com/spatie/laravel-permission) | Role separation: student / faculty / admin / registrar — non-negotiable for a system this size |
| [spatie/laravel-model-states](https://github.com/spatie/laravel-model-states) | Admission pipeline state machine (applied → verified → admitted → enrolled → graduated) |
| [maatwebsite/excel](https://github.com/SpartnerNL/Laravel-Excel) | Bulk marks upload/download, attendance import from biometric/RFID exports |
| [barryvdh/laravel-dompdf](https://github.com/barryvdh/laravel-dompdf) or [spatie/laravel-pdf](https://github.com/spatie/laravel-pdf) | Marksheets, admit cards, transcripts, ID cards |
| [spatie/laravel-activitylog](https://github.com/spatie/laravel-activitylog) | Audit trail — mandatory for marks/attendance edits (academic integrity, dispute resolution) |
| [spatie/laravel-medialibrary](https://github.com/spatie/laravel-medialibrary) | Admission documents, photos, certificates |
| Attendance at scale: Kafka (`mateusjunges/laravel-kafka`) or Redis Streams, not direct DB writes | If attendance is captured via biometric/RFID at thousands of scan events per minute across campus, direct synchronous DB writes will choke — queue the events, batch-write |
| [dedoc/scramble](https://github.com/dedoc/scramble) | If SIS exposes an API to the booking system / mobile app — keep the OpenAPI spec accurate across 5 projects |

### Cross-Cutting (shared across all 5 projects)
| Need | Package/Approach |
|---|---|
| Single sign-on across all 5 Laravel apps | [laravel/passport](https://laravel.com/docs/passport) as a central OAuth2 server, or [workos/workos-php](https://github.com/workos/workos-php) for SSO — one auth service, not 5 separate login systems |
| Shared UI kit across projects | [filamentphp/filament](https://github.com/filamentphp/filament) for all admin panels — consistent look/UX across hostel/transport/hall/SIS admin screens with one shared design system |
| Inter-service communication | Kafka (`mateusjunges/laravel-kafka`) — SIS enrolls a student → event → hostel/transport systems react (auto-allocate room, activate transport pass) without tight coupling |
| Shared config/secrets across 5 deployments | Not a package — a shared `.env` management strategy (Vault, or even a private Composer package holding shared config helpers) matters more at 5-project scale than any single package |

## Docker at This Scale

| Piece | Notes |
|---|---|
| [laravel/sail](https://laravel.com/docs/sail) | Fine for local dev, **not** what you run in production at 500k req/sec — don't confuse the two |
| Multi-stage Dockerfile with FrankenPHP base image | Production image should build once, run everywhere — Octane+FrankenPHP in the container, not PHP-FPM |
| Docker Compose for local multi-service dev (5 apps + Redis + Postgres + Kafka) | Practical for local dev across 5 interconnected Laravel projects; **not** what you'd run in prod at this scale — prod needs orchestration (see below) |
| Kubernetes / Nomad, or your own Porter (Firecracker microVM) | At 500k req/sec across 5 services, plain `docker run` on a few boxes isn't enough — you need real orchestration for autoscaling, rolling deploys, health-checked restarts. This is exactly the problem your own Porter project is aimed at — worth using your own tooling here rather than reaching for vanilla Coolify/Dokploy, which are built for much smaller scale. |
| PgBouncer | Mandatory in front of Postgres at this write volume — see Database Infra section above |
| Redis Sentinel or Redis Cluster | A single Redis instance backing Horizon queues + cache + sessions will itself become the bottleneck at this scale — needs HA/clustering |

**Bottom line on Docker + 500k req/sec + 5 Laravel projects**: the container runtime (Docker) is the easy part. The hard part is orchestration and traffic shaping across 5 services with shared identity/auth and an event bus tying them together — that's an infra design problem your existing Porter/dispatchd-go work is already positioned to solve better than any Composer package list can.

## License

[MIT](LICENSE)
