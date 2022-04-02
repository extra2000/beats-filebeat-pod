# Changelog

## [2.0.0](https://github.com/extra2000/beats-filebeat-pod/compare/v1.1.0...v2.0.0) (2022-04-02)


### ⚠ BREAKING CHANGES

* SSL cert mounting has changed

### Features

* **dockerfile:** upgrade Filebeat from `8.0.0` to `8.1.0` ([4ebfe42](https://github.com/extra2000/beats-filebeat-pod/commit/4ebfe42f34da462b03810fc92db6bcc7300d5e44))


### Code Refactoring

* change SSL to OpenSSL style ([316b5d6](https://github.com/extra2000/beats-filebeat-pod/commit/316b5d6be7abc3a3d92bfe9c1d9fb12b66681df9))
* rename default `es-master-01` to `es-master` ([d93f078](https://github.com/extra2000/beats-filebeat-pod/commit/d93f07808c512b115f9dd90aab673924e88bca03))


### Documentations

* **deployment:** add `chmod` fix for `modules/` ([78636ac](https://github.com/extra2000/beats-filebeat-pod/commit/78636ac44a9b6faae03eede6a7a84b6671939967))
* **deployment:** remove instructions for cert bundle ([4f4a855](https://github.com/extra2000/beats-filebeat-pod/commit/4f4a855dbe4695dd3cab2bb7297041019fb0f6db))
* **nginx:** add example path for logs ([5d3928d](https://github.com/extra2000/beats-filebeat-pod/commit/5d3928da6e6cf6168ae43985faa2632140cc65db))

## [1.1.0](https://github.com/extra2000/beats-filebeat-pod/compare/v1.0.0...v1.1.0) (2022-02-21)


### Features

* **dockerfile:** upgrade Filebeat from `7.16.2` to `8.0.0` ([9f38296](https://github.com/extra2000/beats-filebeat-pod/commit/9f38296cf05d8854d1c4388b3457c24032a325d5))
* **modules:** add NGINX filebeat module ([32d60bc](https://github.com/extra2000/beats-filebeat-pod/commit/32d60bc67e9826579667b7910e678d8d423eb185))

## 1.0.0 (2022-01-04)


### Features

* initial implementations ([99d7a25](https://github.com/extra2000/beats-filebeat-pod/commit/99d7a25339f66df41f4f32cbacbe3da40fc3fa32))


### Documentations

* **README:** update `README.md` ([9bc39d1](https://github.com/extra2000/beats-filebeat-pod/commit/9bc39d1dd3d187ab240ae9d4ff2846df8c3c9bae))


### Continuous Integrations

* add AppVeyor with `semantic-release` ([060102b](https://github.com/extra2000/beats-filebeat-pod/commit/060102bc8cafac3d032a1b4e717dc35dd41d9ad0))
