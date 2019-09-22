# entropic-hello-world

This is a test run of the `entropic` federated package manager.

https://github.com/entropic-dev/entropic

https://youtu.be/MO8hZlgK5zc


## Steps taken:

1. Installed `ds`:
https://github.com/entropic-dev/entropic/blob/master/docs/installing/README.md

2. Ran `ds login` : this created an `~/.entropicrc`. I had to modify mine by prepending the line:
    ```ini
    registry="https://registry.entropic.dev"
    ```

3. Created Package.toml: I then manually copied and pasted the [provided](https://github.com/entropic-dev/entropic#packages) `Package.toml` and prefixed the dependencies with `registry.`, e.g.:
    ```ini
    [dependencies]
    "legacy@registry.entropic.dev/figgy-pudding" = "^3.5.1"
    ```
4. Looked at dependencies via `ds packages`, https://registry.entropic.dev/v1/packages, https://registry.entropic.dev/v1/packages/package/legacy@registry.entropic.dev/chalk
5. Added the `chalk` dependency.
6. Ran `ds build`: this created a `ds` dir and a `node_modules` subdir.
7. Created `program.js`.
8. Ran `node program.js`; it worked 🎉
9. Ran `ds publish`; it told me I didn't have permissions for `entropic.dev`, so I modified `Package.toml` to point to `registry.entropic.dev` instead. Then `ds publish` again, it redirected me to create another login token. I did that, then `ds publish` succeeded and my package now shows up at `ds packages` 🎉🎉🎉
