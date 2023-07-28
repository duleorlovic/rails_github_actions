# Rails Github Actions

This simple configuration will run rails test and system tests also, you just
need to configure headless chrome
https://github.com/duleorlovic/rails_capybara_selenium#ci
and since ubuntu-latest already includes chrome it will run the tests:

```
# https://github.com/duleorlovic/rails_github_actions/tree/main/.github/workflows/minimum_test.yml
```

## Artifacts

If you need to inspect some output of the tests you can use artifact to debug
logs and screenshots

```
# .github/workflows/test.yml
    - name: Run tests
      run: |
        bundle exec rails test:system || echo continue
    - name: Upload Artifact
      uses: actions/upload-artifact@v2
      with:
        name: my-artifact
        # https://github.com/actions/upload-artifact#upload-using-multiple-paths-and-exclusions
        path: |
          tmp/screenshots/*
          doc/screenshots/*
          log/*
```
