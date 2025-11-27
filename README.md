# MuseScore Framework

The maintainers of MuseScore wanted to improve MuseScore's UI and UX. The framework they had been using for the UI, QtWidgets, wasn't flexible enough for they needs. So they decided to switch to QtQuick, a similar but more readable and flexible framework also developed by Qt.

QtQuick and its language QML is more flexible, but it's also harder to make look native to desktop since it was designed around mobile. So, they built MuseScore framework: a set of UI widgets and data structures that let them build MuseScore 4.

Later on, the same company that maintains MuseScore bought Audacity. They had the same intention to improve its UI. So they thought of using the same framework that they built for MuseScore.

However, framework was tied to MuseScore, and it was hard to decouple.

A temporary solution was routinely copying MuseScore's framework into a temporary repository, which was then pulled as a submodule from Audacity. This involves some problems.

## Why this exists

A better solution would be to create a stable, minimal framework that is usable not only to MuseScore but to a wider range of applications. That framework can then be used by MuseScore, Audacity, Advanced Effects or any other application, which extends the framework to each their own needs.

- Minimal dependencies
- Easy to setup
- Available documentation

