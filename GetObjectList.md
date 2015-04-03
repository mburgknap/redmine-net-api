## Returns a paginated list of type T. ##
The default page size is 25. The maximum page size is 100.

#### Parameters: ####
  * offset: skip this number of issues in response (optional)
  * limit: number of issues per page (optional)
  * sort: column to sort with. Append :desc to invert the order.
  * page: page number (optional). You can used instead of "offset" and "limit"

#### Optional filters: (Issue) ####

  * project\_id: get issues from the project with the given id, where the id is either project id or project identifier

  * tracker\_id: get issues from the tracker with the given id

  * status\_id: get issues with the given status id only. Possible values:    open, closed, `*` to get open and closed issues, status id

  * assigned\_to\_id: get issues which are assigned to the given user id

  * cf\_x: get issues with the given value for custom field with an ID of x. (Custom field must have 'used as a filter' checked.)

  * created\_on: fetch issues for a date range.

#### Example: ####

```
using System;
using System.Collections.Specialized;
using Redmine.Net.Api;
using Redmine.Net.Api.Types;

namespace RedmineTest
{
    class Program
    {
        static void Main(string[] args)
        {
            string host = "";
            string apiKey = "";

            var manager = new RedmineManager(host, apiKey);

            //parameter - get all issues
            var parameters = new NameValueCollection {{"status_id", "*"}};

            //parameter - fetch issues for a date range
            parameters.Add("created_on", "><2012-03-01|2012-03-07");

            foreach (var issue in manager.GetObjectList<Issue>(parameters))
            {
                Console.WriteLine("#{0}: {1}", issue.Id, issue.Subject);
            }
        }
    }
}

```

Getting the total issues that are available

```
using System;
using System.Collections.Specialized;
using Redmine.Net.Api;
using Redmine.Net.Api.Types;

namespace RedmineTest
{
    class Program
    {
        static void Main(string[] args)
        {
            string host = "";
            string apiKey = "";

            var manager = new RedmineManager(host, apiKey);

            //parameter - get all issues
            var parameters = new NameValueCollection {{"status_id", "*"}};
int totalItems;

var items = manager.GetObjectList<Issue>(parameters, out totalItems);

            Console.WriteLine("Total items: {0}", totalItems);
            foreach (var issue in )
            {
                Console.WriteLine("#{0}: {1}", issue.Id, issue.Subject);
            }
        }
    }
}

```

Getting all the issues that are available (it will be available in 0.7 version):

```
using System;
using System.Collections.Specialized;
using Redmine.Net.Api;
using Redmine.Net.Api.Types;

namespace RedmineTest
{
    class Program
    {
        static void Main(string[] args)
        {
            string host = "";
            string apiKey = "";

            var manager = new RedmineManager(host, apiKey);

            //parameter - get all issues
            var parameters = new NameValueCollection {{"status_id", "*"}};
          
            foreach (var issue in manager.GetTotalObjectList<Issue>(parameters))
            {
                Console.WriteLine("#{0}: {1}", issue.Id, issue.Subject);
            }
        }
    }
}

```