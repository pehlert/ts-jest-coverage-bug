# How to run

Run `npm install` followed by `npm run test`.
This will run `jest` with ts-jest and the `--collectCoverage` option.

# Observed behaviour

The `src/broken.ts` file is not loaded during testing but required for the coverage collection.
It's transpilation will fail due to a broken import in line 1 (any other typescript error should result in the same behaviour).

The jest command will then exit with code 1 and no further output.

# Expected behaviour

The jest command should log the TypeScript error to stderr before exiting with code 1.

