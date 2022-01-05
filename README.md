# PDFmerger.jl

[![Build Status](https://github.com/scheidan/PDFmerger.jl/actions/workflows/CI.yml/badge.svg?branch=main)](https://github.com/scheidan/PDFmerger.jl/actions/workflows/CI.yml?query=branch%3Amain) [![Coverage](https://codecov.io/gh/scheidan/PDFmerger.jl/branch/main/graph/badge.svg)](https://codecov.io/gh/scheidan/PDFmerger.jl)



A simple tool to merge pdf files on all platforms.

## Usage

#### Merge pdf files

```Julia
merge_pdfs(["file_1.pdf", "file_1.pdf", "file_2.pdf"], "merged.pdf")
```
Note, files can be multiple times.

Use the `cleanup` option to only keep `merged.pdf`:
```Julia
merge_pdfs(["file_1.pdf", "file_1.pdf", "file_2.pdf"], "merged.pdf", cleanup=true)
```

#### Append to a file

Appending with `append_pdf!` is particularly useful to create a single pdf
containing many plots on separate pages:
```Julia
using Plots

for i in 1:5
    p = plot(rand(33), title="$i");
    savefig(p, "temp.pdf")
    append_pdf!("allplots.pdf", "temp.pdf", cleanup=true)
end
```
All plots are contained in `allplots.pdf` and the temporary file is deleted.