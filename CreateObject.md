## Creating an object of type T. ##

When trying to create an object with invalid or missing attribute parameters, you will get RedmineException that contains the corresponding error messages.


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
            string host = "your host";
            string apiKey = "your api key";

            var manager = new RedmineManager(host, apiKey);

            Issue issue = new Issue();
            issue.Project = new IdentifiableName() { Id = 1 };
            issue.Priority = new IdentifiableName() { Id = 4 };
            issue.Subject = "Example";
            issue.Description = "Description";
            issue.Category = new IdentifiableName() { Id = 2 };
            issue.Status = new IdentifiableName() { Id = 3 };
            issue.AssignedTo = new IdentifiableName() { Id = 12 };
            issue.ParentIssueId = 50;

            manager.CreateObject(issue);

        }
    }
}


```