# Formal specification of the SpatialData file format

This repository intends to formalize the SpatialData file format specification. It is encoded as both natural language using the [RFC 2119 terminology](https://datatracker.ietf.org/doc/html/rfc2119), and as JSON schema files, to ensure clarity and machine-readability.

## Specification overview

The SpatialData file format leverages multiple existing projects from the imaging and single-cell communities, to define a complete and language-agnostic representation of spatial omics data.

It offers an harmonized and fully FAIR (Findable, Accessible, Interoperable, and Reusable) approach to managing spatial omics data, which proprietary data formats proposed by each commercial platform, do not achieve.

At its core, SpatialData data has 5 components. Any of these components is optional and a fully conformant can include even a single one of them: 

- `images`: Raster images, typically representing the spatial context of the sample.
   - Elements from this component MUST be [OME-NGFF multiscales](https://ngff.openmicroscopy.org/specifications/0.5/index.html#multiscales-metadata).
   - **NOTE**: currently, SpatialData uses a hybrid format including 0.5 and 0.6 elements. It is named `0.6-dev-spatialdata`.
   - The JSON schemas for these elements is defined in https://github.com/ome/ngff-spec/tree/main/schemas.
- `labels`: Annotations or segmentations of the images, often used to identify regions of interest.
   - Elements from this component MUST be [OME-NGFF labels](https://ngff.openmicroscopy.org/specifications/0.5/index.html#labels-metadata).
   - **NOTE**: currently, SpatialData uses a hybrid format including 0.5 and 0.6 elements. It is named `0.6-dev-spatialdata`.
   - The JSON schemas for these elements is defined in https://github.com/ome/ngff-spec/tree/main/schemas.
- `points`: Discrete spatial coordinates, such as the locations of individual cells or molecules.
- `shapes`: Geometric shapes, such as polygons or lines, representing spatial features.
    - Elements from this component MUST be a parquet file with 
- `tables`: Tabular data associated with the spatial entities, such as gene expression or metadata.
    - Elements from this component MUST be anndata Zarr objects.

