# List Available Cancer Types

Show available cancer types for each reference dataset

## Usage

``` r
list_cancer_types(reference = NULL)
```

## Arguments

- reference:

  Reference dataset name ("precog", "tcga", "pediatric_precog",
  "ici_precog"). If NULL, shows all.

## Value

Named list of cancer types for each reference

## Examples

``` r
if (FALSE) { # \dontrun{
# List all cancer types
list_cancer_types()

# List only TCGA cancer types
list_cancer_types("tcga")
} # }
```
