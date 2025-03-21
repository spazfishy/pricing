# pricing
Processing Instructions
1. Correct MSRPs

    Input: Original MSRP values (e.g., many at $800) are often inaccurate.
    Action: Adjust to realistic values based on brand, specs (CPU/GPU), and release year.
    Output: Whole numbers without $ (e.g., 1500 instead of $1500).

2. Refine Years

    Input: Original Year values may be incorrect.
    Action: Update using CPU/GPU release timelines (e.g., 11th Gen Intel ≈ 2021, RTX 4080 ≈ 2023/2024) and historical product data.

3. Estimate Current Prices

    Model: Calculate Estimated Price based on:
        Age: From March 21, 2025 (current date), with base percentages:
            GPU Laptops: <2y (70%), 2–2.75y (45–75%), 3–3.75y (40–50%), 4–5y (30–40%), 6–7y (20–25%), 8–9y (15–25%), 10+y (10–15%).
            Non-GPU: <2y (50%), 2–2.75y (25–35%), 3–3.75y (15–25%), 4–5y (20–30%), 6–7y (12–17%), 8–9y (6–10%), 10+y (5–8%).
        Adjustments:
            GPU boosts (e.g., RTX 4090: $800, RTX 4080: $300).
            CPU (±$50 for i9/pre-7th Gen).
            Premium ($150/$100 for top/mid-tier).
            Brand boost (+5% for Alienware, Asus ROG, MSI Titan, Origin, Sager, Gigabyte AORUS).
            -10% discount.
        Output: Add Estimated Price (numeric) and Notes (e.g., "GPU, RTX 4080 boost").

4. Title Preservation

    Rule: The Title column must remain exactly identical to the original CSV, character-for-character, with no changes to text, spacing, punctuation, or formatting. Do not edit, reformat, or normalize Title in any way.
    Action: Treat Title as a raw, uneditable string. Copy it directly from the source to the output.
    Extra Info: If additional details (e.g., spec clarifications) are needed, append them to the Notes column only.

5. Chunking

    Size: Process in 100-row chunks (header + 99 laptops for Chunk 1, 100 laptops per chunk thereafter, except the last chunk with 99 total).
    Total Chunks: 64 (63 chunks of 100 rows, final chunk of 99 rows).
    Start: Begin with Chunk 1 (rows 1–100).

6. Output

    Format: CSV text per chunk, with 6 columns: Title, Brand, MSRP, Year, Estimated Price, Notes.
    Header: Include the header (Title, Brand, MSRP, Year, Estimated Price, Notes) only in Chunk 1 (rows 1–100). Omit the header from all subsequent chunks (2–64).
    Delivery: Start with Chunk 1 (rows 1–100), then proceed with chunks 2–64 (100 rows each, no header) upon request.
    Final Step: Combine all chunks into a single CSV, using the Chunk 1 header as the only header, for upload to https://github.com/spazfishy/pricing.

Instructions for Processing

    Start: Load https://raw.githubusercontent.com/spazfishy/pricing/refs/heads/main/masterlistdemo.csv.
    Task: Update MSRPs (whole numbers, no $), refine years, apply pricing model, and add Estimated Price, Notes. Do not modify the Title column—keep it identical to the original CSV; add any extra info to Notes.
    First Step: Process Chunk 1 (rows 1–100) with the header (Title, Brand, MSRP, Year, Estimated Price, Notes) and deliver as CSV text. Confirm the first 5 Title values match the raw CSV before proceeding (e.g., "Acer Predator Triton 300 Intel Core i7 11th Gen Nvidia RTX 3070 Laptop", etc.).
    Next Steps: Continue with chunks 2–64 (100 rows each, no header) as requested.
