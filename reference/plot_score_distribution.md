# Plot Score Distribution

Simple histogram of score distribution using ggplot2

## Usage

``` r
plot_score_distribution(
  scores,
  score_column = NULL,
  main = "Score Distribution",
  base_size = 14
)
```

## Arguments

- scores:

  Numeric vector or data.frame of scores

- score_column:

  If scores is data.frame, which column to plot

- main:

  Plot title

- base_size:

  Base font size for the plot (default 14)
