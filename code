import csv

def read_csv_fieldnames(filename, separator, quote):
    """
    Inputs:
      filename  - name of CSV file
      separator - character that separates fields
      quote     - character used to optionally quote fields
    Output:
      A list of strings corresponding to the field names in 
      the given CSV file.
    """    
    with open(filename, 'r') as file:
        reader = csv.DictReader(file, delimiter = separator, quotechar = quote)
        fieldnames = reader.fieldnames
    
    return fieldnames

def read_csv_as_list_dict(filename, separator, quote):
    """
    Inputs:
      filename  - name of CSV file
      separator - character that separates fields
      quote     - character used to optionally quote fields
    Output:
      Returns a list of dictionaries where each item in the list
      corresponds to a row in the CSV file.  The dictionaries in the
      list map the field names to the field values for that row.
    """
    out_list = []
    with open(filename, "r", newline='') as csvfile:
        row_reader = csv.DictReader(csvfile, delimiter=separator,
                                    quotechar=quote, quoting=csv.QUOTE_MINIMAL)
        for row in row_reader:
            out_list.append(row)
    return out_list

def read_csv_as_nested_dict(filename, keyfield, separator, quote):
    """
    Inputs:
      filename  - name of CSV file
      keyfield  - field to use as key for rows
      separator - character that separates fields
      quote     - character used to optionally quote fields
    Output:
      Returns a dictionary of dictionaries where the outer dictionary
      maps the value in the key_field to the corresponding row in the
      CSV file.  The inner dictionaries map the field names to the
      field values for that row.
    """
    out_dict = {}
    list_dict = read_csv_as_list_dict(filename, separator, quote)
    for my_dict in list_dict:
        key = my_dict[keyfield]
        out_dict[key] = my_dict
    return out_dict

def write_csv_from_list_dict(filename, table, fieldnames, separator, quote):
    """
    Inputs:
      filename   - name of CSV file
      table      - list of dictionaries containing the table to write
      fieldnames - list of strings corresponding to the field names in order
      separator  - character that separates fields
      quote      - character used to optionally quote fields
    Output:
      Writes the table to a CSV file with the name filename, using the
      given fieldnames.  The CSV file should use the given separator and
      quote characters.  All non-numeric fields will be quoted.
    """
    with open(filename, 'w', newline='') as csvfile:
        row_writer = csv.DictWriter(csvfile, delimiter=separator,
                                    fieldnames=fieldnames,
                                    quotechar=quote,
                                    quoting=csv.QUOTE_NONNUMERIC)
        row_writer.writeheader()
        for my_row in table:
            row_writer.writerow(my_row)

