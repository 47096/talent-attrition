# Who is about to leave?

**A talent risk problem, solved with people data.**

Replacing a leaver can cost **50–200% of salary**. HR usually finds out at the resignation email. I help teams see **who is at risk earlier** — so retention conversations happen before the offer letter.

---

## The stake

Attrition is expensive and slow to notice. Engagement surveys are lagging. Exit interviews are too late. The question is not “do we have a retention problem?” It is **“who should we talk to this quarter?”**

## The story

You have people data: satisfaction, performance review, hours, projects, tenure, promotions, accidents.

Instead of a dashboard of averages, I built a **binary classifier** — stayed vs left — and then asked *why*:

1. **Benchmark many models** quickly (don’t guess the algorithm)  
2. **Pick a strong one** (random forest here)  
3. **Tune it**  
4. **Explain it** with SHAP — what actually drives risk  
5. **Score** a holdout so you know it generalises  

**Outcome on this build:**
- Full workflow from raw table → tuned model → **explainable risk drivers**  
- Focus on **actionable signals** (satisfaction, load, tenure), not black-box scores alone  
- Same pattern fits **customer churn** (you already have that case study) and HR retention  

> **The commercial idea:** retention budget goes to the people most at risk — not to everyone who is mildly unhappy.

---

## What that looks like in your world

| You have | I turn it into |
|----------|----------------|
| HRIS / survey / review exports | **Risk scores** per employee |
| “We lose good people every year” | **Who** + **why** (drivers) |
| Retention offers for everyone | A short **priority list** for managers |
| Model nobody trusts | SHAP-style **explanation** for the CHRO |

**Typical engagement:** define “leave” in your window → build scores on your data → manager-ready list + the levers (hours, recognition, promotion lag).

**[Talk to me about retention →](https://datafying.co/#contactus)** · [datafying](https://datafying.co/)

---

## Why people & product leaders bring me in

- Speaks **cost of replacement** and manager actions, not AutoML slang  
- Shows **what drives leaving** so HR can fix the system, not just flag names  
- Fast model comparison without a six-month data science programme  
- Clear ethics/limits: score ≠ punishment; use for support  

---

## Proof of craft *(technical)*

### Job
Binary classification: `left` ∈ {0, 1}.

### Workflow (PyCaret)
```
setup → compare_models → create_model('rf') → tune_model
→ plot_model / evaluate_model → interpret_model (SHAP)
→ predict_model → finalize_model
```

| Stage | Detail |
|-------|--------|
| Data | Employee attrition (PyCaret built-in) — satisfaction, evaluation, hours, projects, tenure, promotion |
| Best model | Random Forest after multi-model benchmark |
| CV | 10-fold |
| Interpretation | SHAP |

### Why this stack
- **Speed** — answer the business question in one sitting  
- **Comparison** — 10+ classifiers before committing  
- **Explainability** — leadership can read the drivers  

### Limits (honesty)
- Built-in demo data — **your** HR definitions and fairness rules must replace it  
- Don’t use scores to punish; use them to **support**  
- Legal/privacy review before scoring real people  
- Drift: retrain when the org changes  

---

## Reproduce

```bash
git clone https://github.com/47096/talent-attrition.git
cd talent-attrition
pip install -r requirements.txt
jupyter notebook analysis.ipynb
```

**Stack:** Python · `pycaret` · `shap`

---

## Next step

If leavers are costing you budget and manager time — that is the engagement I run.

**[Book a conversation →](https://datafying.co/#contactus)** · Customer & people analytics · [datafying](https://datafying.co/)
