# Wikipedia article ToC to GFM task list

This template converts ToC of a Wikipedia article to GFM task list markup.

## Usage

1. From the Wikipedia article webpage, activate the Smart TOC addon and
   select the Menu > Copy... > Copy as JSON option from the ToC panel
1. Save the JSON data to the "data.json" file in this directory
1. Refer [the data.json.sample sample data file](data.json.sample) to
   add an additional "headings" data structure to the first line and
   the last line to the data.json file.
1. Edit [the template.j2 Jinja2 template file](template.j2) to set the
   Wikipedia article's URL to the `url` variable assignment at the top
   of the file
1. Launch a text terminal application
1. Change the working directory to the directory containing this README
1. Run the following command to convert the JSON format ToC data to GFM
   task list markup:

    ```bash
    j2_opts=(
        # The input data is in JSON format
        -f json

        # Output result to an external file
        -o output.md
    )
    j2 \
        "${j2_opts[@]}" \
        template.j2 \
        data.json
    ```

1. The resulting markup should now be in the [output.md](output.md)
   file, ignore the `-o` command option to output to the standard output
   device instead
