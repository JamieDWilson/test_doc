---
layout: default
title: Governing Equations
parent: Model Description
nav_order: 2
---

# Governing Equations
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## PO4 and Dissolved Organic Phosphorus (DOP)

The default state variables are phosphate (PO$_4$) and dissolved organic phosphorus (DOP).

$$ \frac{d\text{PO}_4}{dt} = \mathbf{A} \text{PO}_{4} - \underbrace{\big( J_{up}^{POP} + J_{up}^{DOP} \big)}_{\text{Net export production -} J_{up}}+ J_{remin}^{POP} + J_{remin}^{DOP} + J_{force}^{PO4} $$
