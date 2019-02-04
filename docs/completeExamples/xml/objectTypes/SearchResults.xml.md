# `<SearchResults>`

User is viewing a set of search results independently of the search event that generated them.
The Query/Id element can be used to link the two events together.

This object type can be used when the results of the query are not know at the time the search is executed and the Search event is created.

A View event is used here simply to illustrate the use of SearchResults.
SearchResults can be used within other schema actions.

``` xml
<?xml version="1.0" encoding="UTF-8"?>
<Events
  xmlns="event-logging:3"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="event-logging:3 file://event-logging-v3.4-beta.1.xsd"
  Version="3.4-beta.1">

  <!-- View/SearchResults event -->

  <Event>

    <EventTime>
      <TimeCreated>2017-01-02T03:04:05.678Z</TimeCreated>
    </EventTime>

    <EventSource>
      <System>
        <Name>Rock Sample Database</Name>
        <Environment>Space</Environment>
        <Organisation>ACMECoolResearch</Organisation>
        <Version>R8.1</Version>
      </System>
      <Generator>db-query</Generator>
      <Device>
        <HostName>db56.serverfarm.mydomain.org</HostName>
        <IPAddress>191.181.171.161</IPAddress>
      </Device>
      <Client>
        <HostName>desktop4.moonbase-a.mydomain.org</HostName>
        <IPAddress>111.101.101.111</IPAddress>
      </Client>
      <User>
        <Id>jc101</Id>
      </User>
      <Interactive>true</Interactive>
    </EventSource>

    <EventDetail>
      <TypeId>viewSearchResults</TypeId>
      <Description>User is viewing a set of stored search results</Description>
        <View>
          <SearchResults>
            <Query>
              <!-- 
              Provides a link back to the Search event generated when the 
              query was executed
              -->
              <Id>query-538393</Id>
            </Query>
            <TotalResults>2</TotalResults>
            <Results>
              <Object>
                <Type>Rock</Type>
                <Id>78121</Id>
                <Name>Surpisingly Heavy Chunk</Name>
              </Object>
              <Object>
                <Type>Rock</Type>
                <Id>11418</Id>
                <Name>Possible Gold Ore</Name>
              </Object>
            </Results>
          </SearchResults>
        </View>
    </EventDetail>

  </Event>

</Events>

```