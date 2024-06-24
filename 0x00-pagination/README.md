# 0x00. PaginationResources

This project aims to implement different pagination techniques for a dataset using Python, focusing on a dataset of popular baby names stored in `Popular_Baby_Names.csv`.

## Read or Watch

- [REST API Design: Pagination](https://restfulapi.net/pagination/)
- HATEOAS (Hypermedia as the Engine of Application State)

## Learning Objectives

By the end of this project, you should be able to explain:

- How to paginate a dataset using simple `page` and `page_size` parameters.
- How to implement hypermedia pagination with metadata.
- How to ensure deletion-resilient pagination.

## Setup

Use the data file `Popular_Baby_Names.csv` provided in this repository for the project.

## Tasks

The project includes the following tasks (details can be found in the project description):

1. Simple helper function
2. Simple pagination
3. Hypermedia pagination
4. Deletion-resilient hypermedia pagination

Each task focuses on progressively implementing pagination techniques using the provided dataset.

## Implementation

The project includes a Python script (`3-hypermedia_del_pagination.py`) that demonstrates deletion-resilient hypermedia pagination.

## Usage

To run the project, ensure Python 3.x is installed and execute the scripts provided. Adjust parameters as needed for testing different pagination scenarios.

## Dependencies

- Python 3.x
- `csv` module

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

Special thanks to [RESTful API](https://restfulapi.net/) for their valuable resources on API design and pagination.
