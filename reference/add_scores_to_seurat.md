# Add Scores to Seurat Object

Convenience function to add scores directly to Seurat metadata. Use the
**original** (non-subset) Seurat object so that all genes are retained
for downstream analyses (e.g. cell type marker gene analysis).

## Usage

``` r
add_scores_to_seurat(seurat_obj, scores, prefix = "")
```

## Arguments

- seurat_obj:

  Seurat object (the same full object passed to `PhenoMap`)

- scores:

  Data.frame of scores (output from PhenoMap)

- prefix:

  Prefix for metadata column names (default: "")

## Value

Seurat object with scores added to metadata
