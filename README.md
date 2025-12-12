<h1 align="center">Predicting Mental Health Episodes from Smartphone
Behavior</h1>

<p align="center">
  STA 221 – Big Data &amp; High Performance Statistical Computing (Fall 2025)
</p>

---

## Project Overview
<a href="https://drive.google.com/drive/folders/1BJniOv4sc95MdB7UdWg_caX9FLUaCSHZ?usp=drive_link"
   target="_blank" rel="noopener noreferrer" aria-label="Open Google Drive folder">
  Dataset
</a>

<ul>
  <li><b>Goal:</b> Predict whether a student is <i>depressed</i> or <i>not depressed</i>.</li>
  <li><b>Inputs:</b>
    <ul>
      <li>Mental health questionnaires: PHQ‑9, PSS (perceived stress), PSQI (sleep quality).</li>
      <li>Smartphone‑derived features: screen time, app usage, activity, GPS, calls/SMS.</li>
    </ul>
  </li>
  <li><b>Task type:</b> Binary classification (depressed vs not depressed).</li>
  <li><b>Main models:</b> Logistic regression with
    <ul>
      <li>L1 regularization (LASSO) – sparse, interpretable feature selection.</li>
      <li>L2 regularization (Ridge) – baseline comparison.</li>
    </ul>
  </li>
</ul>

---

## Data

<p>
The raw data are not included in this repository due to privacy restrictions. The analysis assumes access to:
</p>

<ul>
  <li><b>Survey files</b>
    <ul>
      <li>PHQ‑9 (depression)</li>
      <li>PSS (perceived stress)</li>
      <li>PSQI (sleep quality)</li>
    </ul>
  </li>
  <li><b>Sensing files (per user)</b>
    <ul>
      <li>Phone lock / unlock logs</li>
      <li>App usage logs</li>
      <li>Activity logs (still, walking, running, etc.)</li>
      <li>GPS location logs</li>
      <li>Call / SMS logs</li>
    </ul>
  </li>
</ul>

### Final Analytic Dataset

<ul>
  <li>Each row corresponds to one student.</li>
  <li><b>Target variable:</b> de>depressed</code> (1 = PHQ‑9 above cutoff, 0 = below cutoff).</li>
  <li><b>Predictors include:</b>
    <ul>
      <li>Survey‑based features: PSS and PSQI summary scores.</li>
      <li>Smartphone features aggregated per user:
        <ul>
          <li>Daily screen time and number of unlocks.</li>
          <li>Daily app event counts.</li>
          <li>Activity counts (still, walking, running, active).</li>
          <li>GPS features (number of points, variance of latitude/longitude, max distance).</li>
          <li>Social features (total and average call duration, number of calls/SMS).</li>
        </ul>
      </li>
    </ul>
  </li>
  <li>User IDs, timestamps, and raw PHQ‑9 totals are removed before modeling to avoid label leakage.</li>
</ul>

---

## Key Results (Summary)

<ul>
  <li>LASSO achieves high performance on the held‑out test set (ROC–AUC around 0.98 in our runs), with strong recall for the depressed class.</li>
  <li>Ridge performs worse on the depressed class despite similar overall accuracy.</li>
  <li>The most predictive features include:
    <ul>
      <li>Perceived stress (PSS score) and sleep quality (PSQI).</li>
      <li>Average and total call duration.</li>
      <li>GPS mobility measures.</li>
      <li>Activity counts and phone usage measures.</li>
    </ul>
  </li>
</ul>

