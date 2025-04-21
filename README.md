# analyze-eye-tracking-data

A Python pipeline for analyzing pupillary light reflex (PLR) data from eye-tracking tests.

## Project Overview

This project provides tools and scripts for analyzing pupillary light reflex data collected from eye-tracking experiments. The analysis pipeline is designed to process raw data, extract meaningful insights, and generate visualizations.

### Science Background

The pupillary light reflex (PLR) is a physiological response where the pupil constricts or dilates in response to changes in light intensity. This reflex is controlled by the autonomic nervous system and provides valuable insights into neurological and ocular health. By analyzing PLR data, researchers can study various conditions, including brain injuries, neurological disorders, and visual impairments.

- Data cleaning and preprocessing (removal of invalid frames, handling missing data)
- Blink detection and filtering
- Jitter removal using Savitzky-Golay filtering
- Signal quality assessment (precision, stability score, overall quality)
- Advanced pupil metrics calculation
- Visualization of eye tracking data

## Documentation

The following documents are available in the `docs` folder:

- **[Landmark Definitions]():** Provides definitions and explanations of key landmarks used in the analysis.
- **[Ideas](docs/ideas.md):** Development ideas and notes about signal processing techniques.


## Data

The `plr_data` folder contains raw data files organized by unique identifiers. Each subfolder corresponds to a specific dataset.

## Getting Started

To get started with the project:

1. Clone the repository:
   ```bash
   git clone https://github.com/lejrn/analyze-eye-tracking-data.git
   ```
2. Install dependencies using Poetry:
   ```bash
   poetry install
   ```
3. Run the notebook "notebooks/backbone.ipynb"

## Contributing

Follow the [Code Style Guidelines](.github/copilot-codeGeneration-instructions.md) for consistent and maintainable code. Use the commit message template provided in [Commit Message Instructions](.github/copilot-commit-message-instructions.md).

## License

This project is intended for non-commercial use. A specific license has not yet been chosen.
