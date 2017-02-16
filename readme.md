<<<<<<< HEAD
### Operon documentation site

This is source for the Operon documentation site. It is a statically generated Jekyll site. To get a working build environment you'll need ruby <= 2.3. Then from the project root:

```bash
gem install bundler
bundle install
```

Then to build the site to the default `_site` directory run:

```bash
bundle exec jekyll build
```

Or (from the project root) you can run the supplied build script:

```bash
scripts/build
```

Then to deploy using rsync to the server:

```bash
scripts/deploy
```

You will need SSH access to web server docs.operon.cloud, also in order to make the site redeployable for others without intervention you will need sudo access on the web server (to chown the copied files)

#### Full build and deployment

Run:

```bash
scripts/build && scripts/deploy
```

#### TODO
- Set up CI environment to deploy from master (e.g. CircleCI)
||||||| merged common ancestors
=======
### Operon documentation site

This is source for the Operon documentation site. It is a statically generated Jekyll site. To get a working build environment you'll need ruby <= 2.3. Then from the project root:

```bash
gem install bundler
bundle install
```

Then to build the site to the default `_site` directory run:

```bash
bundle exec jekyll build
```

Or (from the project root) you can run the supplied build script:

```bash
scripts/build
```

Then to deploy using rsync to the server:

```bash
scripts/deploy
```

You will need SSH access to web server docs.operon.cloud, also in order to make the site redeployable for others without intervention you will need sudo access on the web server (to chown the copied files)

#### TODO
- Set up CI environment to deploy from master (e.g. CircleCI)
>>>>>>> Add readme
