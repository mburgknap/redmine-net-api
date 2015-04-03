## Updating an object of type T. ##

When trying to update an object with invalid or missing attribute parameters, you will get RedmineException that contains the corresponding error messages.


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

            var issue = manager.GetObject<Issue>("1", null);
            issue.Description = "Updated description"; 

            manager.UpdateObject(issue);

        }
    }
}


```