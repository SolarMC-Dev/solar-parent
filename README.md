
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

### Changelog

1.0.0

* Normalized properties to use `kebab-case`. Prior to this release, the properties followed a format using "solar-parent." followed by the property name in lowerCamelCase, for example, `solar-parent.jdkVersion`.
* Set the preparationGoals of the maven-release-plugin to a no-op goal. This reflects the expectation that releases are performed automatically by a CI server. For deployment by hand, it is suggested to reset the preparationGoals setting to "clean verify". In most cases the release process should be transferred to the responsibility of the automatons.

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

