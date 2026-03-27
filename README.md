# aqi-asthma-montecarlo
learning and simulating monte carlo
# AQI–Asthma Risk: Monte Carlo Simulation

A probabilistic model exploring how uncertainty in Air Quality Index (AQI) propagates into a simulated respiratory risk score.
This project combines environmental variability, human exposure, and biological sensitivity into a unified risk framework.

Note: This is an educational project and not a clinical or diagnostic tool.
This model is intended for academic exploration of uncertainty and probabilistic modeling.
It is not a medical or diagnostic tool.


---

## Model Overview

The system models risk as an interaction of three components:

* AQI (Environment): Sampled from a normal distribution
* Exposure (Behavior): Uniform distribution [0.5, 1.5]
* Sensitivity (Biology): Beta distribution (2, 5)

Risk Function:

```
raw = (AQI / 500) * Exposure * Sensitivity
risk = sigmoid(raw - 0.5)
```

This formulation captures how incremental increases in pollution can lead to nonlinear increases in risk beyond a threshold.

---

## Outputs

The simulation generates:

* Input distributions (AQI, Exposure, Sensitivity)
* Sigmoid transfer function
* Risk distribution (Normal vs High AQI scenarios)
* Cumulative distribution (CDF)
* 30-day AQI vs risk time series

---

## Data Sources

| Component       | Source                                                          | Type           |
| --------------- | --------------------------------------------------------------- | -------------- |
| AQI values      | CPCB India — cpcb.nic.in *(or fallback statistical parameters)* | REAL / ASSUMED |
| Exposure factor | `np.random.uniform(0.5, 1.5)`                                   | Synthetic      |
| Sensitivity     | `np.random.beta(2, 5)`                                          | Synthetic      |

---

## Running the Project

Open the notebook in Google Colab:

```
AQI_Asthma_Simulation.ipynb
```

No installation is required.

---

## Technology Stack

Python • NumPy • Matplotlib • Google Colab

---


## Interpretation Highlights

* **Higher AQI shifts risk distribution rightward**, increasing probability of severe outcomes
* **Wide distributions indicate uncertainty** due to variability in exposure and sensitivity
* **Sigmoid function introduces threshold behavior**, where risk rises sharply beyond a point
* **CDF plots highlight worst-case scenarios (tail risk)**
* **Time series shows risk dynamically tracking AQI fluctuations**

These insights demonstrate how environmental uncertainty propagates into health risk variability.

