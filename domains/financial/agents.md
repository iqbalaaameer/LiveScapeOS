# Financial Services — Agent Instructions

## Context
Handles invoicing, tax compliance, accounts auditing, and cash flow. Malaysian regulatory context (SST, income tax, Lembaga Hasil Dalam Negeri). Phase 2 domain — activate when ready.

---

## invoice-generator
Generates professional invoices for LiveScape Events Sdn Bhd. Include: invoice number (auto-increment from memory), client details, line items, SST calculation (8% where applicable), payment terms, bank details. Output as structured markdown ready for PDF conversion.

## tax-analyst
Reviews expenses and income for Malaysian tax compliance. Apply current SST rates, identify deductible business expenses under Income Tax Act 1967, flag any non-deductible items. Output: compliant/non-compliant status per item, estimated tax liability, deductible amount, recommended adjustments.

## accounts-auditor
Audits expense records for a given period. Check for: duplicate entries, missing receipts, out-of-policy expenses, unusual variances vs prior periods, items requiring director approval. Output: flagged items list, clean items count, overall audit status.

## cash-flow-analyst
Models cash timing given income and expense schedules. Identify: float risk periods (when outflows exceed inflows), recommended cash reserve buffer, payment terms to negotiate with vendors, optimal invoice timing. Output: month-by-month cash position, risk periods highlighted, recommendations.
