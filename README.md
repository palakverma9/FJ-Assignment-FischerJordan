# Shipment Cost Normalization Analysis
### FischerJordan Data Analytics Assignment

## Overview
Analysis of parcel invoice data for a shoe company shipping 4 lb parcels 
across India via carriers like Delhivery, DTDC, Blue Dart, FedEx, etc.

The goal was to design a normalized shipment cost model for fair 
comparison of shipping costs across carriers.

---

## Dataset
- **Total Records:** 214
- **Unique Shipments:** 106
- **Carriers:** 9 (Delhivery, DTDC, Blue Dart, FedEx, Gati, Ekart Logistics, DHL, Ecom Express, Safe Express)
- **Zones:** 6
- **Unique Charge Types:** 196
- **Missing Values:** None

---

## Approach

### Charge Classification
All 196 charge types were grouped into 5 categories:

| Category | Included in Normalized Cost? | Reason |
|----------|------------------------------|--------|
| Base Rate | ✅ Yes | Core carrier charge |
| Operational Surcharge | ✅ Yes | Unavoidable, applies to all carriers |
| Tax & Customs | ❌ No | Government imposed, not carrier's pricing |
| Penalty/Correction | ❌ No | Shipper's fault, avoidable |
| Optional/Special Service | ❌ No | Shipper elected, not carrier's decision |

### Normalization Formula
```
Normalized Cost = Base Rate + Operational Surcharge
```
For 104/106 shipments with no Base Rate → Total Cost was used as fallback.

---

## Key Findings

1. **Ekart Logistics** is cheapest at 8.98/lb
2. **Safe Express** is costliest at 14.34/lb
3. **50.3% of spend** is on Optional/Special Services — largely avoidable
4. **17.2% of spend** is Penalties/Corrections — completely avoidable waste
5. **Worst 10% shipments** (16 out of 106) = 36.1% of total spend
6. **Zone 4** has highest cost spread — riskiest zone for budgeting

---

## Recommendations
- Replace Safe Express and FedEx with Ekart Logistics where possible
- Audit all Optional/Special Service charges for necessity
- Fix address correction issues to reduce penalty charges
- Negotiate special rates for Zone 4 shipments

---

## Assumptions & Limitations
- 104/106 shipments had no Base Rate — Total Cost used as proxy
- Normalization did not change carrier rankings in this dataset
- Weight inconsistencies (4 lbs vs 4) were cleaned programmatically
- Zone inconsistencies (Zone 3 vs 3) were standardized
- AI tools were used for guidance in structuring the analysis

---

## Files
| File | Description |
|------|-------------|
| `FJ_Assignment.ipynb` | Main Jupyter Notebook with full analysis |
| `FJ_Assignment.csv` | Original dataset |
| `FJ_Assignment_Final.csv` | Processed shipment summary |

---

## Tools Used
- Python 3
- Pandas
- Matplotlib
- Jupyter Notebook

---

*Submitted by: Palak Verma | March 2026*
