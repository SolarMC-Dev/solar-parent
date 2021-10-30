
## Solar-Parent

Parent pom to reduce commonly-needed configuration.

### Properties

Available properties. Defaults are reasonable and may be overridden in `<properties>`.

* `solar-parent.jdk-version` - Sets the JDK version, 16 by default.
* `solar-parent.enable-preview` - Set this to "--enable-preview" to enable preview feature support. Disabled by default.
* `solar-parent.skip-javadoc` - Set this to true to disable javadoc creation
* `solar-parent.skip-sources` - Similar to prior, but for sources
* `solar-parent.auto-version-submodules` controls maven-release-plugin's autoVersionSubmodules, true by default.
* `solar-parent.asm-version` - Sets the ASM version used in several places. Important for JDK updates.

### Requirements

1. State license in pom and during deployment.
  * Accepted licenses are Affero GPL v3, GPL v3, Lesser GPL v3, and private/closed-source.
  * Child poms should declare a `<licenses>` attribute and include the license they use. 
  * During deployment, one of the following profiles must be activated: `deploy-affero-gpl3`, `deploy-gpl3`, `deploy-lesser-gpl3` or `deploy-internal`.
2. Avoid the use of third-party repositories. 
  * It is recommended to keep the repositories used to Maven Central and the SolarMC repository.
  * Most child poms should comply with this restriction.
  * If absolutely necessary, this restriction can be bypassed by configuring `<phase>none</phase>` for the maven-enforcer goal with id `<id>enforce-organization-repositories</id>`.
3. Deploy via "continuous delivery," such that the build server runs the entire build and verifies success before deploying. In most cases the release process should be the responsibility of the automatons.
  * Usually requires SCM configuration.
  * This expectation is realized in the configuration of the maven-release-plugin, which is suited for the expected release workflow: configure SCM, run `mvn release:prepare release:clean`, and the build server automatically builds and deploys the release version.
  * In the rare case that manual deployment is necessary, configure the `preparationGoals` of the maven-release-plugin to "clean verify". Then configure SCM and use `mvn release:prepare release:perform`.

### Semver Meaning

Since this is not software written in an imperative programming language with a clear concept of an API, solar-parent follows a certain meaning to
its versioning:

* **Major** versions are for breaking changes; that is, changes which remove or alter functionality of existing stable configurations.
* **Patch** versions are either invisible improvements or bug-fixes to correct unintended or unspecified behavior. These are very rare since Maven is declarative.
* **Minor** versions are for everything in between. This includes new functionality and configuration options. It also includes feature additions like plugin updates. Since most builds are stable and do not rely on deprecated plugin features, solar-parent may upgrade maven plugins in minor versions. It is therefore possible, but unlikely, for minor versions to truly break a build.

### Changelog

1.1.1

* Removed solar-repo as pluginRepository since it is no longer needed

1.1.0

* Added oss-gpl3 deployment profile which deploys under the GNU General Public License v3 or later

1.0.0

* Updated to JDK 17 by default
* Require better licensing practice from child poms.  Added 3 deployment-related profiles for each 3 licenses.
* Restrict the use of third-party repositories by default.
* Normalized properties to use `kebab-case`. Prior to this release, the properties used lowerCamelCase after the period, for example, `solar-parent.jdkVersion`.
* Set the preparationGoals of the maven-release-plugin to a no-op goal. This reflects the expectation that releases are performed automatically by a CI server.
* Updated plugin versions

0.6.2

* Enable apiNote, implSpec, and implNote javadoc tags

0.6.1

* Changed repository URLs to mvn-repo.solarmc.gg

0.6.0

* Preview features now disabled by default.
* Javadocs and sources now enabled by default.

0.5.8

* Added pluginRepositories
* Added a property to disable preview features
* Removed javadoc:javadoc goal; only javadoc:jar is needed
* Changed execution IDs for maven-failsafe-plugin (organized configuration)

0.5.7

* Added maven-assembly-plugin common configuration

0.5.6

* Added ASM re-specification for maven-dependency-plugin

0.5.5

* Added maven-invoker-plugin common configuration

0.5.4

* Added more configuration for maven-release-plugin

0.5.3

* Added maven-release-plugin
* Added propertiesEncoding for copying resources

