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
[data caching workflow](https://github.com/clusterflick/data-cached)
completes successfully. It can also be triggered manually via workflow dispatch
if needed.

## Downstream Triggers

After successfully combining the data, this workflow triggers:

- [data-matched](https://github.com/clusterflick/data-matched) - For enriching
  movie data with additional sources
- [clusterflick.com](https://github.com/clusterflick/clusterflick.com) - To
  update the main website with the latest data
- [analysis.clusterflick.com](https://github.com/clusterflick/analysis.clusterflick.com) - To
  update the analysis site with the latest data

## Maintenance

### Dependencies

The workflow requires API keys configured as GitHub secrets:

- `MOVIEDB_API_KEY` - For fetching movie metadata from The Movie Database
- `PAT` - Personal Access Token for publishing releases and triggering
  downstream workflows
