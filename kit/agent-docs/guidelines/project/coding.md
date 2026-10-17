# Project coding rules

<!-- FILL ME IN. Only rules that are specific to this project. Universal rules
     already live in ../universal/coding.md; do not repeat them here. -->

## Main risk

<One line: what breaks most easily in this project. E.g. "Regressions in shared
pricing logic" or "Schema drift between the five DB projects".>

## Layering

<The actual chain, e.g. Models -> Repositories -> Services -> DTOs/Mappers -> Pages.>

## Localization

- Mechanism: <e.g. `Localizer` with keys in `Resources/Translations*.resx`>
- Files and their locales: <e.g. `Translations.resx` and `.en.resx` = English only; `.it.resx` = Italian only>
- Single-language project? <yes / no — if yes, ignore the localization section of the universal rules>

## Naming and formatting

<Deviations from the language default only.>

## Forbidden zones

<Files, folders, or tables the agent must never change without an explicit spec.>
