# Data Card for the Enterprise Software Products Dataset

## Dataset Description

This natural language dataset contains over 1,000 enterprise software products each classified into a taxonomy. A simple taxonomy is used with only two levels, called categories and sub-categories, that have a non-overlapping 1-to-many parent-child relationship. Each product in the dataset has been assigned a sub-category and it's related parent category. All products, categories, and sub-categories have unique, short natural language descriptions/definitions associated with them. This is a purely English language dataset.

## Dataset Structure

## Data Fields

 - `products.csv`: The main dataset of 1,495 enterprise software products. The column definitions are:
    - `product_name`: The name of the product.
    - `vendor_name`: The name of the vendor as written in the legal contracts with that vendor.
    - `taxonomy_category`: The category from the taxonomy assigned to the product. Must be the parent of the sub-category assigned to this product according to the taxonomy.
    - `taxonomy_sub_category`: The sub-category from the taxonomy assigned to the product. Must be the child of the category assigned to this product according to the taxonomy.
    - `product_description`: A description of the product, which should typically desribe at a high level the primary purpose or function of this product.

 - `categories.csv`: The list of 13 top-level categories in the taxonomy. The column definitions are:
    - `name`: The name of the category.
    - `definition`: A single sentence definition of the kinds of products or features/capabilites of a product that fall under this category.

 - `sub-categories.csv`: The list of 61 sub-categories in the taxonomy. The column definitions are:
    - `parent`: The category that is the parent of the sub-category in the taxonomy. Each category has at least one sub-category, and each sub-category has a single parent.
    - `name`: The name of the sub-category.
    - `definition`: A single sentence definition of the kinds of products or features/capabilites of a product that fall under this sub-category.

## Dataset Creation

### Initial Data Collection & Curation Rationale

This dataset was originally compiled by a team of enterprise architects for the purposes of tracking what software venders were in use within a large (Fortune 500) enterprise. Not included in this dataset is information about whether or not these products were actively in use, retired, or considered but never adopted. Therefore, a product in the dataset is in the dataset because it was at some point considered for use within that enterprise.

### Who are the source language producers?

The language producers are enterprise technology experts in the enterpise archtecture department of a large (Fortune 500) enterprise company. No further demographic information was available from the data source.

### Annotation Process

The classification taxonomy, including category and sub-category names, descriptions, and relationships, were developed by enterprise technology experts in the company. Product category and sub-category selections as well as descriptions were sourced from a vendor's marketing material/website and/or manually created by enterprise technology experts based on their experience with the product.

### Personal and Sensitive Information

To maintain anonymity and confidentiality, all references to the source company or that company's specific or sensitive applications were removed from the source data.

## Considerations for Using the Data

### Social Impact of Dataset

The purpose of this dataset is to help develop classification and generative models that work on enterpise software product descriptions.

A system that succeeds at the supported task would be able to properly assign products into a given taxonomy and help determine which products are related or overlapping in their capabilites.

### Discussion of Biases

The company from within which this dataset was created is intentionally made anonymous so that the dataset can be treated in a generic fashion. However, there may still be some bias towards incuding or excluding certain types of technologies based on what is relevant specific company's industry that may not apply to other companies.

The company is U.S based and all descriptions are in English, which may present a bias if attempting to use in different geographic or language contexts.

## Other Known Limitations:

- While the dataset classfications and descritions were largely curated by enterprise technology experts, it should not necessarily be considered ground truth. The coherence, clarity, and accuracy of the classifications and descriptions across products in this dataset is by no means guaranteed. Up-front analysis to discover and correct or filter outliers before further processing or model training is highly recommended.
- While the structure of this dataset may imply there is only once correct choice for each product, this is not necessarily true. For some products, this simple taxonomy may not provide a clear single correct choice, even for experts in that field.
- Theorecically, the multicharacter strings columns in this dataset can be of any length. Practically, there is a limit to the number of characters in each string, but the limit is an arbitrary restriction imposed by the relational database that stores tha data and does not have any inherent meaning.
- The vendor names of a company are based on legal contracts only. This name may be very different than the commonly referred to name of said company. Applications which could benefit from attaching a commonly known name to the product or knowing if one legal entity is a parent or child of another may need an external dataset in order to make that association.
