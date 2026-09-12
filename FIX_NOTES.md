# Staff Promotion Prediction Fix Notes

## Fixed

- Added Python 3.12 deployment pinning and compatible binary-wheel dependencies.
- Made dataset and runtime-cache paths relative to `app.py`.
- Added clear Google Drive download failure handling.
- Added stale/corrupt runtime-cache recovery so the app can retrain instead of failing at startup.
- Added visible model-build error reporting.
- Preserved the documented 2025 reference year used by the training workflow, rather than allowing the prediction definition to drift with the calendar year.

## Runtime behavior

The app still trains the Random Forest on first startup because the repository does not contain a deployable serialized pipeline. This may take approximately 60 seconds on a cold start. The next production improvement should be offline training and committing/versioning a complete fitted pipeline.
