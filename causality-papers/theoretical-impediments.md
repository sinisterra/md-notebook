# Theoretical Impediments to Machine Learning with seven sparks from the Causal Revolution

## Abstract

Most Machine Learning systems are model-free, which limits their performance because the lack of reasoning about intervention and retrospection. Machines need a model of reality. The paper then explains some tasks that can only be done with a Causal Model.

## Scientific Background

Machine Learning is statistic-driven, but this capability on its own does not enable features such as producing alternative hypotheses or planning.
Mental representations of the environment are important, because they enable questions such as **interventions**: What if I act? and **restrospective or explanatory ones**: What if I had acted differently. Current Machine Learning models cannot produce such interventions right now.

## The three layer causal hierarchy

1. Counterfactuals (Why?)
2. Interventions (What if I do?)
3. Association (What?)

Association relies on conditional probabilities.
Intervention: Do randomized clinical trials, Causal Bayesian Networks
Counterfactuals: Structural Equation Models

Any curve-fitting, no matter how complicated, does not leave the first rung of the causal ladder (association)

## Seven Pillars of the Causal Revolution

Cause-effect questions did not have the benefit of mathematical analysis until Structural Causal Models were defined.

### Structural Causal Models

Structural Causal Models are defined by three main elements:

- **graphical models**: these describe the assumptions, what is known.
- **counterfactual and interventional logic**: describe what we want to know.
- **structural equations**: interaction between what is known and what we want to know.

**Elements**

- **query**: the question to be answered
- **estimand**: formula based on the assumptions, capable of answering the query
- **estimation**: use the estimand and the data to provide an answer
- **graphical model**: assumptions
- **fit indices**: how well does the graphical model describe the data
- **data**: observations

**Process**

1. Use the query the graphical model to produce an estimand (function)
2. Use the estimand and the data to produce an estimation (value)
3. Report fit indices (how well the data is described by the assumptions)

### Encoding causal assumptions

Causal Models offer transparency (check how plausible the assumptions are), and testability (check compatibility of the model with the data).

### Do-calculus and control of confounding

Select which covariates should be used to control/adjustment set.

### Counterfactual algoritmization

Structural equations determine the value of a counterfactual.
These also allow understanding the causes of effects and the effects of causes.

### Mediation Analysis

Show direct and indirect effects from the data. Check how much of the ffect of X on Y is mediated by Z.

### External Validity and Sample Selection Bias

Allow domain-adaptation.

### Missing Data

Causal Models can help if the missing data relations are expressed with a causal model.

### Causal Discovery

Infer the models that are compatible with the data. Causal queries can be estimated directly from the set of compatible models.

## Conclusion

Science has favoured metaphisical models instead of rigid, black-box ones. Model-based approaches are essential for some tasks that lead to Strong AI. Data science needs to link data to the real world to be truly useful.
