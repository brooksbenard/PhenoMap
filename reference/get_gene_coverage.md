# Get Gene Coverage

Check which genes from your data are covered in reference datasets

## Usage

``` r
get_gene_coverage(genes, reference = NULL)
```

## Arguments

- genes:

  Character vector of gene names

- reference:

  Reference dataset(s) to check. If NULL, checks all.

## Value

Data.frame with gene coverage statistics

## Examples

``` r
if (FALSE) { # \dontrun{
# Check gene coverage
my_genes <- c("TP53", "MYC", "EGFR", "BRCA1")
get_gene_coverage(my_genes)
} # }
```
