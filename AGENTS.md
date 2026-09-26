# Asset Sync Instructions

This Ruby/Rails gem synchronizes precompiled assets to Fog-compatible storage. `lib/` owns synchronization and configuration, `spec/unit/` supplies isolated cases, and `spec/integration/` exercises storage providers. The Gemfile pins Rails 4.1.5, so use a compatible legacy Ruby/Bundler environment rather than assuming a current Ruby will install it. Run `bundle install`, then use `bundle exec rake spec:unit` for a local unit check. The default task invokes `spec:all`: it runs integration tests when `TRAVIS != 'true'`, or when both `TRAVIS == 'true'` and `TRAVIS_PULL_REQUEST == 'true'`, so it can perform AWS-backed upload and deletion work.

Do not run the default task for routine validation. Never commit credentials, bucket names, or customer manifests. Completion for a code change is the unit result; remote upload/delete scope and readback are separate evidence.
