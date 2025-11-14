# data-combined

This repository contains the automated workflow for combining cinema data for
the Clusterflick project.

## Purpose

The combining workflow aggregates transformed data from all venues into a single
unified dataset. This consolidated data serves as the primary data source for
the Clusterflick application and other downstream consumers.

## How It Works

The workflow executes the combine command to merge all venue data:

```bash
npx clusterflick/scripts combine
```

This command:

- Reads the transformed data from all venues
- Merges the data into a unified format
- Resolves any data conflicts or duplicates
- Generates a combined dataset with consistent structure
- Publishes the combined data as a release

## Schedule

The workflow is automatically triggered when the
[data transformation workflow](https://github.com/clusterflick/data-transformed)
completes successfully. It can also be triggered manually via workflow dispatch
if needed.

## Maintenance

### Dependencies

The workflow requires a GitHub secret:

- `PAT` - Personal Access Token for publishing releases and triggering
  downstream workflows