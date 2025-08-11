# [1.7.0](https://github.com/de-it-krachten/ansible-role-openscap/compare/v1.6.0...v1.7.0) (2025-08-11)


### Features

* Add support for AlmaLinux 10 ([89d4c40](https://github.com/de-it-krachten/ansible-role-openscap/commit/89d4c40f1ef0f12f569da2067255d9c5bb398b8c))
* Add support for OracleLinux 10 ([2044e03](https://github.com/de-it-krachten/ansible-role-openscap/commit/2044e03270235e974036e608dcb96d2ae3a0b35b))
* Add support for Red Hat Enterprise Linux 10 ([855fc7d](https://github.com/de-it-krachten/ansible-role-openscap/commit/855fc7dbf756993b70b625668fca8a54e7af704d))

# [1.6.0](https://github.com/de-it-krachten/ansible-role-openscap/compare/v1.5.1...v1.6.0) (2024-07-12)


### Bug Fixes

* Update RHEL OVAL location ([f15effb](https://github.com/de-it-krachten/ansible-role-openscap/commit/f15effb0cd96071342c1f3b49ac934fd1ed6160e))


### Features

* Add support for OpenSCAP hardening checks ([4b8eae1](https://github.com/de-it-krachten/ansible-role-openscap/commit/4b8eae1ef8a6548e1d5b9d89bf054c2592933c58))
* Add support for Ubuntu 24.04 LTS + Fedora 40 ([38460f3](https://github.com/de-it-krachten/ansible-role-openscap/commit/38460f35f9155f5940759932b52ab2c9b5793a26))
* Support Ubuntu 24.04 LTS ([460bb77](https://github.com/de-it-krachten/ansible-role-openscap/commit/460bb77c323592346b773c769a209202a56b24c7))

## [1.5.1](https://github.com/de-it-krachten/ansible-role-openscap/compare/v1.5.0...v1.5.1) (2024-04-12)


### Bug Fixes

* Change loop/label for latest ansible ([41de6b4](https://github.com/de-it-krachten/ansible-role-openscap/commit/41de6b4407ac36d5c17d5ab099de5c5039327a96))
* Fix 'rmtree' issue ([e04ef7c](https://github.com/de-it-krachten/ansible-role-openscap/commit/e04ef7cf6b741f1de24a53923af98121220d9bd0))

# [1.5.0](https://github.com/de-it-krachten/ansible-role-openscap/compare/v1.4.0...v1.5.0) (2023-09-17)


### Bug Fixes

* Fix loop label to string ([6d75699](https://github.com/de-it-krachten/ansible-role-openscap/commit/6d75699e37e825c883f6d68bcea11f7201cc6537))


### Features

* Update supported platforms & CI ([a19e5dc](https://github.com/de-it-krachten/ansible-role-openscap/commit/a19e5dcdb9751b1d4122932845bdbc0ef4bd56f0))

# [1.4.0](https://github.com/de-it-krachten/ansible-role-openscap/compare/v1.3.0...v1.4.0) (2023-06-21)


### Bug Fixes

* Report retrieval now by file pattern ([cd9b887](https://github.com/de-it-krachten/ansible-role-openscap/commit/cd9b88777abb6d5ba92d7270360667fb9b0014a6))


### Features

* Add support for Fedora 38 ([b023466](https://github.com/de-it-krachten/ansible-role-openscap/commit/b023466aadcd3533b9d2a4bcfad41a25765feaf8))
* Drop support for Fedora 36 ([f3e6af2](https://github.com/de-it-krachten/ansible-role-openscap/commit/f3e6af2787c8b5b169640c6bfd0366c907aa3df0))

# [1.3.0](https://github.com/de-it-krachten/ansible-role-openscap/compare/v1.2.1...v1.3.0) (2023-06-18)


### Features

* Add nice HTML report ([de9b6f6](https://github.com/de-it-krachten/ansible-role-openscap/commit/de9b6f629c11a65709d03d65bd8deb9b9c153fdb))
* Add support for RockyLinux ([4f89338](https://github.com/de-it-krachten/ansible-role-openscap/commit/4f893384c2f2fc0b37810d0e3e904976d36b9327))

## [1.2.1](https://github.com/de-it-krachten/ansible-role-openscap/compare/v1.2.0...v1.2.1) (2023-05-22)


### Bug Fixes

* Move GPG related configuration to separate role ([64e83fd](https://github.com/de-it-krachten/ansible-role-openscap/commit/64e83fd3f21c5fef3858c2eec272b35e26aeb4e8))

# [1.2.0](https://github.com/de-it-krachten/ansible-role-openscap/compare/v1.1.1...v1.2.0) (2023-05-06)


### Bug Fixes

* Add optional immediate report generation ([7516730](https://github.com/de-it-krachten/ansible-role-openscap/commit/75167302a85cebd507c8496a16701c5f026a5439))
* Make central report location configurable ([56e31e1](https://github.com/de-it-krachten/ansible-role-openscap/commit/56e31e138000bf58c27f8b98dcf4221450531d8e))


### Features

* Move to namespaced role names ([f59a55e](https://github.com/de-it-krachten/ansible-role-openscap/commit/f59a55eeda8fcbf3b0b0db5ab8129dfff79de002))

## [1.1.1](https://github.com/de-it-krachten/ansible-role-openscap/compare/v1.1.0...v1.1.1) (2022-12-20)


### Bug Fixes

* Leave OpenSCAP report on server ([606b562](https://github.com/de-it-krachten/ansible-role-openscap/commit/606b562d793d1b80ff3208b9bc990ed20abd5c60))

# [1.1.0](https://github.com/de-it-krachten/ansible-role-openscap/compare/v1.0.0...v1.1.0) (2022-12-13)


### Features

* Add yum/apt repositories & packages ([1187a29](https://github.com/de-it-krachten/ansible-role-openscap/commit/1187a29f71b7f810112b191a909a69d6703e2075))

# 1.0.0 (2022-12-13)


### Features

* Initial release ([38eae84](https://github.com/de-it-krachten/ansible-role-openscap/commit/38eae84e5817d122db6e33cc430af11949ad08d1))
