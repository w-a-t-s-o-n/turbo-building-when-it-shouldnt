## Repro for https://github.com/vercel/turbo/discussions/7743

### Steps

1. Run `pnpm i` (or `corepack enable` first)
2. Run `pnpm test`

#### Expected
`tokens` and `icons` run `build`, then `design-system` runs `test`

#### Actual
`tokens`, `icons`, and `design-system` run `build`, then `design-system` runs `test`

### Notes

- If you remove the `other-package` from the repo, which has a dependency of `design-system`, it actually does work as expected.  So it appears the issue is related to that package, even though it does not have a `test` script and shouldn't affect this situation.
- If you run `pnpm test -- --filter design-system`, it does work as-expected. 
