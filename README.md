# Clinical Pathway to Hospitalization

## Overview

This project uses Medicare claims, diagnosis, pharmacy, laboratory, and hospitalization data to identify the clinical pathways that precede hospitalization.

Traditional risk models focus on predicting whether a patient will be hospitalized. This project goes a step further by identifying the diagnosis progression patterns, utilization trends, and clinical deterioration pathways that occur before admission.

The objective is to help healthcare organizations move from reactive care to proactive intervention.

---

# Key Question

Instead of asking:

> Which patients are likely to be hospitalized?

This project asks:

> What pathways do patients follow before hospitalization occurs?

---

# Data Sources

The model integrates multiple CMS Medicare Synthetic Public Use Files (SynPUF):

### Beneficiary Files

* Demographics
* Chronic condition indicators
* Eligibility information

### Carrier Claims

* Professional services
* Physician encounters
* Specialty utilization

### Outpatient Claims

* Emergency department utilization
* Outpatient facility services

### Inpatient Claims

* Hospital admissions
* Diagnosis Related Groups (DRGs)
* Length of stay

### Prescription Drug Events (PDE)

* Medication utilization
* Polypharmacy indicators
* Medication escalation patterns

### Laboratory Utilization

* Testing frequency
* Monitoring intensity
* Lab escalation signals

---

# Model Components

## Hospitalization Forecasting Model

Primary prediction target:

```text
Hospitalization within 90 days
```

Performance:

| Metric       | Result |
| ------------ | -----: |
| Training AUC |  0.844 |
| Testing AUC  |  0.839 |
| AUC Gap      |  0.005 |

Training was performed using Medicare SynPUF Samples 1 and 2.

External validation was performed using Sample 3.

---

## Clinical Pathway Mining

The project identifies diagnosis progression pathways that historically precede hospitalization.

Examples include:

```text
Stroke/TIA → CKD → AKI

CKD → AKI → Cellulitis

UTI → Dehydration → AKI

Pneumonia → CKD → AKI

Sepsis → Cellulitis → AKI
```

---

# Major Findings

Baseline 90-day hospitalization risk:

```text
4.5%
```

Patients exposed to high-risk diagnosis pathways:

```text
15%
```

Patients with the highest pathway exposure:

```text
~20%
```

This represents approximately:

```text
3x–4x higher hospitalization risk
```

compared to the baseline population.

---

# Highest-Risk Clinical Pathways

Examples discovered during pathway mining:

| Pathway                          | Hospitalization Rate |
| -------------------------------- | -------------------: |
| Cellulitis → Stroke/TIA → Sepsis |                35.7% |
| Sepsis → Cellulitis → AKI        |                29.2% |
| CKD → Asthma → Sepsis            |                27.2% |
| CHF → Asthma → Sepsis            |                26.2% |
| UTI → Dehydration → AKI          |                25.8% |

---

# Key Insight

Many high-risk pathways converged around:

* Chronic Kidney Disease (CKD)
* Acute Kidney Injury (AKI)

The analysis suggests kidney deterioration frequently serves as a bridge between chronic illness, infection, and hospitalization.

Examples:

```text
UTI → Dehydration → AKI

Pneumonia → CKD → AKI

Stroke/TIA → CKD → AKI

Sepsis → Cellulitis → AKI
```

---

# Potential Applications

### Population Health

* Early identification of deteriorating patients
* Risk stratification

### Care Management

* Intervention prioritization
* High-risk work queues

### Utilization Management

* Admission prevention strategies
* Resource allocation

### Medicare Advantage

* Cost reduction initiatives
* Hospital avoidance programs

### PACE Programs

* Interdisciplinary team prioritization
* Early clinical intervention

---

# Future Enhancements

Planned enhancements include:

* Provider intelligence scoring
* Specialty referral pathway mining
* Lab trajectory modeling
* Multi-window hospitalization forecasting
* Skilled nursing facility forecasting
* Cost-of-care prediction
* Explainable AI pathway recommendations

---

# Disclaimer

This project was developed using CMS Medicare Synthetic Public Use Files (SynPUF) for educational, research, and model development purposes. Results should not be interpreted as clinical recommendations without validation using production healthcare data.

---

# Author

Pablo Lau

Healthcare Operations | Population Health | Predictive Analytics | Artificial Intelligence

Focused on leveraging data science and machine learning to identify actionable opportunities for improving healthcare outcomes and reducing avoidable utilization.
