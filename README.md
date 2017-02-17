### Operon documentation site

This is source for the Operon documentation site. It is a statically generated Jekyll site. To get a working build environment you'll need ruby <= 2.3. Then from the project root (run locally from your development machine):

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

You will need SSH access to web server docs.operon.cloud as the 'deploy' user.

#### Grant deployment access

To grant deployment access to a user on the web server add their SSH public key to the deploy user's `authorized_keys` file:

```bash
cat /home/the_user/.ssh/authorized_keys >> /home/deploy/.ssh/authorized_keys
```

When running the deploy script (on your local machine) make sure you have the ssh agent running (check with `ssh-add`)

#### Full build and deployment

Run:

```bash
scripts/build && scripts/deploy
```

#### TODO
- Set up CI environment to deploy from master (e.g. CircleCI)
