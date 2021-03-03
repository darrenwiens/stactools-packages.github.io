# STAC Extensions

The [stac-extensions](https://github.com/stac-extensions/) github organization is a home for extensions to the
[SpatioTemporal Asset Catalog](https://github.com/radiantearth/stac-spec) specification.

To learn about STAC and Extensions start with the [extensions](https://github.com/radiantearth/stac-spec/extensions)
section of the core specification. It explains how extensions work, lists all the known extensions, and has
instructions for how to go about '[extending STAC](https://github.com/radiantearth/stac-spec/extensions/README.md##extending-stac)'.

The [stac-extensions](https://github.com/stac-extensions/) is a home for many of the leading 'community extensions',
providing a neutral home for collaboration. Many of these used to be in the core [stac-spec
repository]((https://github.com/radiantearth/stac-spec)), but were removed for 1.0.0 so they could evolve at their
own pace, instead of having to follow the core STAC release cycle.

## Extension Maturity

Extensions in this directory are meant to evolve to maturity, and thus may be in different states
in terms of stability and number of implementations. All extensions included must include a
maturity classification, so that STAC spec users can easily get a sense of how much they can count
on the extension.

| Maturity Classification |  Min Impl # | Description | Stability |
| ----------------------- | ----------- | ----------- | --------- |
| Proposal                | 0           | An idea put forward by a community member to gather feedback | Not stable - breaking changes almost guaranteed as implementers try out the idea. |
| Pilot                   | 1           | Idea is fleshed out, with examples and a JSON schema, and implemented in one or more catalogs. Additional implementations encouraged to help give feedback | Approaching stability - breaking changes are not anticipated but can easily come from additional feedback |
| Candidate               | 3           | A number of implementers are using it and are standing behind it as a solid extension. Can generally count on an extension at this maturity level | Mostly stable, breaking changes require a new version and minor changes are unlikely. The extension has a [code owner](../.github/CODEOWNERS). |
| Stable                  | 6           | Highest current level of maturity. The community of extension maintainers commits to a STAC review process for any changes, which are not made lightly. | Completely stable, all changes require a new version number and review process. |
| Deprecated              | N/A         | A previous extension that has likely been superseded by a newer one or did not work out for some reason. | DO NOT USE, is not supported |

Maturity mostly comes through diverse implementations, so the minimum number of implementations
column is the main gating function for an extension to mature. But extension authors can also
choose to hold back the maturity advancement if they don't feel they are yet ready to commit to
the less breaking changes of the next level.

A 'mature' classification level will likely be added once there are extensions that have been
stable for over a year and are used in twenty or more implementations.

## List of STAC Extensions

The definitive list of STAC Extensions is in the core spec repository, in the [Extensions 
README](https://github.com/radiantearth/stac-spec/blob/master/extensions/README.md). This includes the official core
extensions, as well as a complete list of 'community' extensions. A subset of the community extensions use this 
stac-extensions GitHub organization, and those are listed in the next section.

### Extensions in stac-extensions organization

These extensions add new fields or semantics to STAC objects.

| Extension Title                                  | Identifier        | Field Name Prefix   | Scope                     | Maturity   | Status | Description |
| ------------------------------------------------ | ----------------- | ------------------- | ------------------------- | ---------- | ------ | ----------- |
| [Data Cube](datacube/README.md)                  | datacube          | cube                | Item, Collection          | *Proposal* | Repo Created | Data Cube related metadata, especially to describe their dimensions. |
| [File Info](file/README.md)                      | file              | file                | Item, Collection          | *Proposal* | Published* | Provides a way to specify file details such as size, data type and checksum for assets in Items and Collections. |
| [Item Asset Definition](item-assets/README.md)   | item-assets       | -                   | Collection                | *Proposal* | Repo Created | Provides a way to specify details about what assets may be found in Items belonging to a Collection. |
| [Label](label/README.md)                         | label             | label               | Item                      | *Proposal* | Published* | Items that relate labeled AOIs with source imagery |
| [Point Cloud](pointcloud/README.md)              | pointcloud        | pc                  | Item                      | *Proposal* | Repo Created | Provides a way to describe point cloud datasets. The point clouds can come from either active or passive sensors, and data is frequently acquired using tools such as LiDAR or coincidence-matched imagery. |
| [Processing](processing/README.md)               | processing        | processing          | Item, Collection          | *Proposal* | Repo Created | Indicates from which processing chain data originates and how the data itself has been produced. |
| [SAR](sar/README.md)                             | sar               | sar                 | Item                      | *Proposal* | Published* | Covers synthetic-aperture radar data that represents a snapshot of the earth for a single date and time. |
| [Satellite](sat/README.md)                       | sat               | sat                 | Item                      | *Proposal* | Repo Created | Satellite related metadata for data collected from satellites. |
| [Single File STAC](single-file-stac/README.md)   | single-file-stac  | -                   | Catalog                   | *Proposal* | Repo Created | An extension to provide a set of Collections and Items within a single file STAC. |
| [Storage](storage/README.md) | storage | storage | Item | *Proposal* | Repo Created | Provides additional fields relating to how the asset is stored. |
| [Tiled Assets](tiled-assets/README.md)           | tiled-assets      | tiles               | Item, Catalog, Collection | *Proposal* | Repo Created | Allows to specify numerous assets using asset templates via tile matrices and dimensions. |
| [Timestamps](timestamps/README.md)               | timestamps        | -                   | Item                      | *Proposal* | Published* | Allows to specify numerous timestamps for assets and metadata. |
| [Versioning Indicators](version/README.md)       | version           | -                   | Item, Collection          | *Proposal* | Repo Created | Provides fields and link relation types to provide a version and indicate deprecation. |
| [CARD4L](https://github.com/stac-extensions/card4l) | card4l         | card4l.             | Item                      | *Proposal* | Repo Created | How to comply to the CEOS CARD4L product family specifications (Optical and SAR) |

**Status** - Indicates the status of the extension moving out of STAC Core to the `stac-extensions` organization. Status is one of:

- *Blank* - repo has not yet been created
- Repo Created - Repo has been created from template
- Updated - Contents have been updated with extension from STAC Core
- Reviewed - Extension has been reviewed (should happen priopr to Published)
- Published - Release made, schemas published
- Published* - Release made, schemas published, but was not reviewed

## Adding a new extension

### Using the stac-extensions template

TODO: Overview of using the template.

Step-by-step (add an image or two)

* Request to become a member of stac-extensions if you want to it to have that visibility, or put in your personal or org's repo
* Go to [template repo](https://github.com/stac-extensions/template) and hit the green 'Use this template' button.
* Be sure to pick the right place to create it.
* Description - briefly describe it
* click 'copy all branches' for the CI to write correctly.
* Title your table properly - likely is just item properties or collection fields, though some are both. But make your heading clear.
* Schemas - start with the templates, and add in your properties.
* In 'settings' turn on github pages (unless we find a way to do this automatically) - probaby add a picture for this.
