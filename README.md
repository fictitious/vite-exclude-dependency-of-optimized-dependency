

```sh
yarn install
vite
```

This monorepo has 3 packages:

- `test-package-e` is the main package which imports both `test-package-e-included` and `test-package-e-excluded`
- `test-package-e-included` is the first level dependency which also imports `test-package-e-excluded`
- `test-package-e-excluded` is the leaf dependency imported by the previous 2 packages

`test-package-e-included` is in `optimizeDeps.include`

`test-package-e-excluded` is in `optimizeDeps.exclude`

`test-package-e-excluded` uses a property on a window object to count how many times the package has been loaded,
and returns it as a result of exported `testExcluded()` function, which is shown in the `index.html` page

When you run `vite` in development mode, is shows that the package was loaded twice, which I think is a bug in vite.

In production build, the package is loaded only once.



