
## Solar-Parent

Parent pom to reduce commonly-needed configuration.

### Properties

Available properties. Defaults are reasonable and may be overridden in `<properties>`.

* `solar-parent.jdkVersion` - Sets the JDK version, 16 by default.
* `solar-parent.enablePreview` - Set this to "--enable-preview" to enable preview feature support. Disabled by default.
* `solar-parent.skipJavadoc` - Set this to true to disable javadoc creation
* `solar-parent.skipSources` - Similar to prior, but for sources
* `solar-parent.autoVersionSubmodules` controls maven-release-plugin's autoVersionSubmodules, true by default.
* `solar-parent.asmVersion` - Sets the ASM version used in several places. Important for JDK updates.

### Changelog

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

