## Getting an object of type T. ##

#### Parameters: (Issue) ####

> include: fetch associated data (optional).

> Possible values: children, attachments, relations, changesets and journals.

To fetch multiple associations use comma (e.g ?include=relations,journals).

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

            //parameter - fetch associated relations.
            var parameters = new NameValueCollection {{"include", "relations"}};
      

            var issue = manager.GetObject<Issue>("1", parameters);
            Console.WriteLine("#{0}: {1}", issue.Id, issue.Subject);
        }
    }
}
```