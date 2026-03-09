# Add Scores to SingleCellExperiment Object

Convenience function to add scores to SCE colData. Use the **original**
(non-subset) SCE object so that all genes are retained for downstream
analyses (e.g. marker genes).

## Usage

``` r
add_scores_to_sce(sce_obj, scores, prefix = "")
```

## Arguments

- sce_obj:

  SingleCellExperiment object (the same full object passed to
  `PhenoMap`)

- scores:

  Data.frame of scores (output from PhenoMap)

- prefix:

  Prefix for colData column names (default: "")

## Value

SingleCellExperiment object with scores in colData
