# Wikipedia article ToC to GFM task list

This template converts ToC of a Wikipedia article to GFM task list markup.

## Usage

1. From the Wikipedia article webpage, activate the Smart TOC addon and
   select the Menu > Copy... > Copy as JSON option from the ToC panel
1. Save the JSON data to the "data.json" file in this directory
1. Edit [the template.j2 Jinja2 template file](template.j2) to set the
   Wikipedia article's URL to the `url` variable assignment at the top
   of the file
1. Launch a text terminal application
1. Change the working directory to the directory containing this README
1. Run the following command to convert the JSON format ToC data to GFM
   task list markup:

    ```bash
    jinjanate_opts=(
        # The input data is in JSON format
        -f json

        # Set name to the array of the data file
        --format-option array-name=headings

        # Output result to an external file
        -o output.md
    )
    jinjanate \
        "${jinjanate_opts[@]}" \
        template.j2 \
        data.json
    ```

1. The resulting markup should now be in the [output.md](output.md)
   file, ignore the `-o` command option to output to the standard output
   device instead

## References

The following third-party materials were referenced during the writing of this document.

* [Options | JSON | Data Formats | kpfleming/jinjanator: Jinja2 Command-Line Tool, reworked, again](https://github.com/kpfleming/jinjanator?tab=readme-ov-file#options-2)  
  Explains the `array-name` JSON data input format option.
