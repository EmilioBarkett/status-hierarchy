# Status Hierarchies in Language Models

[![arXiv](https://img.shields.io/badge/arXiv-2601.17577-b31b1b.svg)](https://arxiv.org/abs/2601.17577)

Code, results, and paper source for [*Status Hierarchies in Language Models*](https://arxiv.org/abs/2601.17577) (Barkett, 2026), a Master's thesis in Media Studies / Sociology at Columbia University.

## Research question

Status hierarchies, rank orderings based on respect and perceived competence, are a universal feature of human social organization. Language models trained on human text encounter these patterns constantly. Do they reproduce status dynamics in multi-agent settings? In particular, do models defer to a partner because of status cues rather than task information?

## Method

The experiment adapts the expectation states design of [Berger, Cohen & Zelditch (1972)](https://doi.org/10.2307/2093465) to language models.

- **Task.** Two model instances, M1 and M2, rate the sentiment of the same movie review, drawn from IMDb or Rotten Tomatoes.
- **Four phases per trial.** (1) Independent rating. (2) Introduction to the partner's status characteristics. (3) Revelation of both initial ratings. (4) An opportunity to keep or revise the rating.
- **Status manipulation.** Status is conveyed through credential descriptions in each model's system prompt, such as education, occupation, and prestige. Unlike the original design, these characteristics are task-relevant.
- **Dependent variable.** Deference: the rate at which a model shifts its rating toward its partner's, based on status cues rather than task information.
- **Design.** A 2 × 4 × 2 factorial design crossing model type (same or different models), status assignment (standard, reversed, equal, or none), and dataset (IMDb or Rotten Tomatoes).

## Repository layout

```
status-hierarchy/
├── paper/                    # Thesis LaTeX source: chapters, figures, and tables
├── run_experiment.py         # Entry point: runs the experiment and the analysis
├── experiment.py             # One trial through the four phases
├── prompts.py                # Prompts for each phase
├── config.py                 # Models, conditions, status profiles, and dataset
├── api_client.py             # Model API client
├── data_handler.py           # Loads reviews and saves results
├── analyze_results.py        # Deference rates and plots
├── statistical_analysis.py   # Statistical tests
├── requirements.txt
└── results/                  # Per-condition trial CSVs, summary statistics, and plots
```

Files in `results/` named `condition{N}_{...}_imdb` hold the IMDb trials for one condition, with `-v1` and `-v2` variants of each. `experiment_results_{date}` files are individual timestamped runs.

## Author and advisors

- **Emilio Barkett**, Columbia University (author)
- **James Chu**, Columbia University (advisor)
- **David M. Markowitz** (advisor)

## Citation

```bibtex
@misc{barkett2026status,
  title         = {Status Hierarchies in Language Models},
  author        = {Barkett, Emilio},
  year          = {2026},
  eprint        = {2601.17577},
  archivePrefix = {arXiv},
  primaryClass  = {cs.HC},
  note          = {Master's thesis, Columbia University}
}
```

## References

- Berger, J., Cohen, B. P., & Zelditch, M. (1972). Status characteristics and social interaction. *American Sociological Review, 37*(3), 241–255.
