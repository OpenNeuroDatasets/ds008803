# Lumbosacral spinal cord task-based fMRI (motor, stretch, tendon vibration) and high-resolution anatomical MRI dataset

Task-based fMRI of the lumbosacral spinal cord during active/passive limb
movement and tendon vibration, together with high-resolution T2-weighted
anatomical scans and physiological recordings.

```
@article{hernandez-charpak_towards_2025,
	title = {Towards personalized mapping through lumbosacral spinal cord task {fMRI}},
	volume = {3},
	issn = {2837-6056},
	url = {https://direct.mit.edu/imag/article/doi/10.1162/imag_a_00455/127406/Towards-personalized-mapping-through-lumbosacral},
	doi = {10.1162/imag_a_00455},
	language = {en},
	urldate = {2025-04-28},
	journal = {Imaging Neuroscience},
	author = {Hernandez-Charpak, Sergio Daniel and Kinany, Nawal and Ricchi, Ilaria and Schlienger, Raphaëlle and Mattera, Loan and Martuzzi, Roberto and Nazarian, Bruno and Demesmaeker, Robin and Rowald, Andreas and Kavounoudias, Anne and Bloch, Jocelyne and Courtine, Grégoire and Van De Ville, Dimitri},
	month = jan,
	year = {2025},
	pages = {imag\_a\_00455},
}
```


## Sessions

- `ses-ankle`, `ses-hip`, `ses-knee`: high-resolution T2-weighted anatomical
  scan(s) plus active/passive extension/flexion task fMRI runs.
- `ses-vibration`: tendon vibration task fMRI runs (ankle, hip, knee).

Note: sub-03 only has the vibration session and sub-10 did not have the vibration session.

## Per-run file set

Every functional run includes:

- `_bold.nii.gz` + `_bold.json` -- the functional MRI data and its
  acquisition parameters.
- `_events.tsv` -- onset/duration/weight of the task condition blocks.
  `ses-vibration` runs additionally have a `trial_type` column
  (`extension`/`flexion`) marking which direction each vibration block
  targeted. (`weight` is a constant block-on marker at 1; see
  `events.json` for both column descriptions.)
- `_physio.tsv.gz` + `_physio.json` -- the synchronized physiological
  recording. Columns are
  `["respiratory", "cardiac", "trigger", "cardiac_filtered"]` sampled at
  100 Hz for every run except sub-09's `ses-ankle` session (a one-off EMG
  test for that subject only), which instead has
  `["EMG_1", "EMG_2", "respiratory", "cardiac", "trigger", "cardiac_filtered"]`
  at 1000 Hz. `cardiac_filtered` is the `cardiac` channel after a causal
  low-pass/smoothing filter (~390ms delay). `StartTime` is negative and
  specific to each run -- the recording starts a few seconds before the
  first fMRI volume.

Every anatomical scan includes `_T2w.nii.gz` + `_T2w.json`. The zoomit T2w were used to trace the invidividual roots to define the personalized spinal levels. (See supplementary figure 1 in the [supplementary materials](https://mitp.silverchair-cdn.com/mitp/content_public/journal/imag/3/10.1162_imag_a_00455/2/imag_a_00455-supp.pdf?Expires=1792186908&Signature=M-QXQEOL93E~-FyMnBK67Ca9lSKa3kpAkEcGNzNkrjzZPfIg~dA0aJ2MB6gdUu0MnykpNeWdpDBAxko-0s9VTUVHcn0MLNWTXLB5KBGZyOsEWcW7RdqvK4iARdwZy4JznQrEkdDjBW6sRKgT5d8fsoYK6yLI9ZATECte5a4wDBL8eUlo2gGjB8m9S50RU1zCFHRHS7w2psBE9IvFQX5p3f~vfMa2zJruk-mUy4~jWoFelJIhYpVug-aPwWw0NmVBvRdKGoCotTxuCn5Vv7yqv69KPc-vcDAY6dBpK2UU-K3DQe4iKcR7NF5tAlbtqVCeYQTxz5nZhdUjjs27dvKPjQ__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA))

- Some subjects have more than a single high-resolution "zoomit" T2w scan to ensure there was at least one good quality scan.
