# Get Top Prognostic Genes

Extract top prognostic genes for a specific cancer type

## Usage

``` r
get_top_prognostic_genes(
  reference,
  cancer_type,
  n = 50,
  direction = c("both", "positive", "negative")
)
```

## Arguments

- reference:

  Reference dataset name

- cancer_type:

  Cancer type label

- n:

  Number of top genes to return (default: 50)

- direction:

  "positive", "negative", or "both" (default: "both")

## Value

Data.frame with genes and their z-scores

## Examples

``` r
if (FALSE) { # \dontrun{
# Get top 100 genes for breast cancer
top_genes <- get_top_prognostic_genes("precog", "BRCA", n = 100)

# Get top negative prognostic genes
bad_genes <- get_top_prognostic_genes("tcga", "LUAD", n = 50, direction = "negative")
} # }
```
