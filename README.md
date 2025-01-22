# SeriesMatrixIO

<!-- badges: start -->
<!-- badges: end -->

The goal of **SeriesMatrixIO** is to provide bioinformaticians with an R-native toolkit for handling Series Matrix files (`.txt` files) with an optional identical output with extension `.seriesmatrix`. These files, commonly used for gene expression data in the Gene Expression Omnibus (GEO), often lack a strict standard for structure and content. SeriesMatrixIO addresses this by offering tools to read, validate, generate, and convert Series Matrix files, while introducing a clear standard for the format.

## Features

- Read series matrix (`.txt`, or as defined in this package, `.seriesmatrix`) files into R as structured objects.
- Validate `.seriesmatrix` (or series matrix-like `.txt`) files against a standardized schema to ensure correctness.
- Generate `.seriesmatrix` files from input data (e.g., metadata, expression matrices) (with optional output to `.txt`).
- Convert `.seriesmatrix` and series matrix-like `.txt` files to and from JSON, YAML, and CSV formats.
- R-friendly utilities for exploring, transforming, and exporting data.

## Installation

You can install the development version of SeriesMatrixIO like so:

```r
if (!require("BiocManager", quietly = TRUE))
    install.packages("BiocManager")

# The following initializes usage of Bioc devel
BiocManager::install(version = "devel")

BiocManager::install("SeriesMatrixIO")
```

or install via github:

```r
if (!requireNamespace("remotes", quietly = TRUE))
    install.packages("remotes")
remotes::install_github("rela-v/SeriesMatrioxIO")
```

## Example
This is a basic example that shows you how to solve a common problem:

```r
library(SeriesMatrixIO)

# Reading a series matrix .txt or .seriesmatrix file
data <- read_seriesmatrix("SERIES_MATRIX_FILENAME.txt")
# OR
data <- read_seriesmatrix("SERIES_MATRIX_FILENAME.seriesmatrix")

head(data$expression)  # Inspect the expression matrix

# Validating a series matrix file in .txt or .seriesmatrix
validate_seriesmatrix("SERIES_MATRIX_FILENAME.txt")
# OR
validate_seriesmatrix("SERIES_MATRIX_FILENAME.seriesmatrix")


# Generating a .seriesmatrix file or a series matrix .txt file
generate_seriesmatrix(
    metadata = "metadata.json",
    expression_data = "expression_data.csv",
    output_file_name = "new_seriesmatrix.txt", # OR `output_file_name = "new_seriesmatrix.seriesmatrix"`
)

# Converting a .seriesmatrix file to JSON
convert_seriesmatrix("example_seriesmatrix.seriesmatrix", to = "json", output = "example.json")
# OR, if .txt, as is most common,
convert_seriesmatrix("example_seriesmatrix.txt", to = "json", output = "example.json")
```

## Documentation

For full documentation and examples, see SeriesMatrixIO vignettes ("SeriesMatrixIO/vignettes/") or visit the BioConductor page.

## Contributing

Suggestions and contributions are welcome! Please visit the GitHub repository to report issues, suggest features, or submit pull requests.

## License
This package is licensed under the GPL v2.0 License. See the LICENSE file for details.
