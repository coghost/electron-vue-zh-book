# 测试

## [Unit testing](unittesting.md)

Run unit tests with Karma + Mocha

```bash
npm run unit
```

## [End-to-end testing](end-to-end_testing.md)

Run end-to-end tests with Spectron + Mocha

```bash
npm run e2e
```

## Running all tests

```bash
npm test
```

### 关于 CI 测试

如果在使用 `vue-cli` 时选择了 `electron-builder`, 那么你可以方便的使用 `Travis CI/AppVeyor` 来测试. 在这两个的配置文件 `.travis.yml/appveyor.yml` 中, 取消相应注释即可. 详情参考 [**Automated Deployments using CI**](/using-electron-builder.md#automated-deployments-using-ci). 