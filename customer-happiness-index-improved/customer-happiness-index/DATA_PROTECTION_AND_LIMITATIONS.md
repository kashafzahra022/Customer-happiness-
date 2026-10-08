# Data protection and limitations

## Data handling (POC)
- Use synthetic or fully anonymized reviews only. Do not load real customer names, account numbers, NRIC/FIN, phone numbers, or card details.
- Review text is stored as entered. Strip personal identifiers before CSV upload.
- Accounts are for POC access only. Passwords are hashed, but this is not banking-grade authentication.

## Regulatory considerations (for a production design, not implemented here)
- Singapore Personal Data Protection Act (PDPA): purpose limitation, consent or legitimate basis for using customer feedback, retention limits, and access/correction requests.
- MAS technology risk management and outsourcing guidelines, if a bank deploys this with a third-party sentiment service.
- Data residency: check where the Supabase/Vercel region stores data before using real customer feedback.

## Accuracy and validity
- Sentiment labels come from VADER with a banking lexicon. Measured accuracy on a fresh 30-review set is 63% (53% without the lexicon). This is below what production use would need.
- CHI is a proposed index. It has not been validated against CSAT or NPS.
- Categories use keyword rules and have not been measured for accuracy.

## Language coverage
- VADER is designed for English. Singlish, Malay, Mandarin, and Tamil reviews are not handled reliably.

## Next steps before production
1. Label 150-200 real or realistic reviews with two annotators and measure agreement.
2. Compare VADER with a fine-tuned transformer on the same labels.
3. Validate CHI against a CSAT or NPS survey.
4. Add multilingual handling and a privacy review under PDPA.
