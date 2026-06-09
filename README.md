# Library of Edgewood

The Library of Edgewood is a curated collection of academic papers, technical documents, and research reviews organized by topic. It serves as a personal knowledge base for collecting, reviewing, and analyzing documents with possible applications within interesting fields — particularly those relevant to AI infrastructure, HPC, and distributed systems.

## Purpose

This repository is intended to:

- **Collect** research papers, technical white papers, and industry studies on topics including (but not limited to):
  - Power management and energy efficiency for AI datacenters
  - Distributed and parallel file systems
  - Storage performance optimization
  - GPU/AI accelerator infrastructure
  - High-performance computing (HPC) architectures
  
- **Review** documents by extracting key findings, summarizing contributions, and identifying actionable insights

- **Analyze** papers for practical application within real-world infrastructure projects

## Structure

```
library_of_edgewood/
├── pdfs/
│   ├── power/           # Power management, energy efficiency papers
│   │   ├── README.md    # Paper reviews with summaries and key findings
│   │   ├── REFERENCES.md # Reference lists from papers
│   │   └── *.pdf        # Source documents
│   ├── storage/         # Distributed/parallel file system papers
│   │   ├── README.md
│   │   ├── REFERENCES.md
│   │   └── *.pdf
│   └── [other topics]/ # Future topic directories
│       └── ...
└── README.md
```

## Documentation Format

Each topic directory contains:

- **README.md** — Structured reviews of each paper including:
  - Summary (2-3 sentence overview + context)
  - Key Findings (numbered list of main insights)
  - Actionable Next Steps (checklist items for follow-up)

- **REFERENCES.md** — Reference lists extracted from papers for further reading

## Adding New Papers

When adding new papers to the collection:

1. Place the PDF in the appropriate topic directory (create a new directory if needed)
2. Use the `library-of-edgewood-processor` skill to create a structured review
3. Update the README.md with the new paper review
4. Extract and add references to REFERENCES.md

## Related Skills

- `library-of-edgewood-processor`: Workflow for processing papers into structured reviews
- `large-scale-nfs-research`: Research on NFS and distributed file systems
- `fio-benchmark-analysis`: Storage benchmarking methodology
- `ocr-and-documents`: PDF text extraction tools

## License

See LICENSE file for details.