Metaname
========

Simple, evolving tool for generating metadata from filenames where embedded
metadata isn't available natively. You name a file in a way which reflects it's
contents, run this script over it to output that information in an
easy-to-read format. It breaks the filenames into segments, and then figures out
what the segments contain.

Segment Definitions:
--------------------

Auto-detected Segments:

**Example filename:** creative\_commons.dir:creative\_commons.lic:creative\_commons.desc:a\_video\_about\_creative\_commons.2017-01-01.s01e01.special.mp4

 * Title:

        Pattern: All un-tagged details in the filename.
        Example: .creative_commons.
        Output Formatting: 'Title: Creative Commons'
        Notes: Multiple titles can be specified by separating un-tagged segments
          with a period.

 * Date:

        Pattern: follows '[0-9]{4}-[0-9]{1,2}-[0-9]{1,2}'
        Example: .2017-01-01.
        Output Formatting: 'Date: 2017-01-01'
        Notes: If a Date is present, a Year will never be printed.

 * Year:

        Pattern: follows '[0-9]{4}'
        Example: .2017.
        Output Formatting: 'Year: 2017'
        Notes: If a Date is present, a Year will never be printed.

Tagged Segments:

 * Director:

        Pattern: contains 'dir:'
        Example: .dir:creative_commons.
        Output Formatting: 'Director: Creative Commons'
        Notes: Nothing special.

* Genre:

        Pattern: contains 'genr:'
        Example: .genr:documentary,educational
        Output Formatting: 'Genre: Documentary,educational'
        Notes: For multi-tagging, comma-separated fields are recommended.

 * Description:

        Pattern: contains 'desc:'
        Example: .desc:a_video_about_creative_commons
        Output Formatting: 'Description: A video about creative commons'
        Notes: Nothing special.

 * License:

        Pattern: contains 'lic:'
        Example .lic:creative_commons.
        Output Formatting: 'License: Creative Commons'
        Notes: Nothing special.

 * Season:

        Pattern: follows 's[0-9]{1,3}'
        Example: .s01
        Output Formatting: 'Season: 01'
        Notes: Must be in conjunction with an episode, e.g. s01e01

 * Episode:

        Pattern: follows 'e[0-9]{1,3}'
        Example e01.
        Output Formatting: 'Episode: 01'
        Notes: Must be in conjunction with an episode, e.g. s01e01
