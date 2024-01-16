# AI assistant for querying data. :material-professional-hexagon:{ .pro title="Available for PRO version only" }

Crafting manual SQL queries for data analytics can be tedious and dull. Fortunately, we have an `AI assistant`
ready to make the process effortless for you. Simply click on the :fontawesome-solid-robot: icon and engage in 
a conversation with the assistant to effortlessly query your data.

Here is an example:

=== "AI assistant for querying data"
    ![AI assistant for querying data](assets/images/smartcsv-ai-assistant.gif){ width="300" loading=lazy }


## How does it work?
The `AI assistant` sends the column names and your query to the OpenAI service, then retrieves the SQL query.
Finally, SmartCSV runs that SQL query locally and displays the data.

## Privacy
- Smart CSV only sends column names and your query to the OpenAI service.
- Your OpenAI API key is saved locally.

## Setup.
To access the AI assistant feature, you first need to upgrade to the `Smart CSV Pro` version.

Secondly, you'll require an OpenAI API key. You can register for a new account and obtain the API key by visiting: [https://platform.openai.com/api-keys](https://platform.openai.com/api-keys).


Finally, you'll need to open the dialog to set up your OpenAI API key.
You can access this dialog by either clicking on the :fontawesome-solid-robot: icon while viewing a CSV file
or by navigating to the Settings screen and clicking on the `Setup AI assistant` button.


Within the Setup dialog, enter your API key into the OpenAI API key text field and then click on the `Save` button.

Now, you are ready to engage with the AI assistant and query your CSV content.