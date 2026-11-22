# Compatibility Adjustments

This reproduction uses the original MANNeR implementation at commit:

`a831482f4d9b4918cb7625aed1c66bb68b6db1fe`

The original repository was developed for an earlier Python and
machine-learning environment. The following compatibility adjustments
were required to run the code in Google Colab with Python 3.13,
PyTorch 2.11/2.14, Lightning 2.6.6, TorchMetrics 1.9.0, and
Transformers 4.57.6.

## 1. Project-root marker

MANNeR calls `pyrootutils` with `.project-root` as the project
indicator. An empty marker was created at:

```text
/content/manner/.project-root
