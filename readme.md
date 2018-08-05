# Indexed Everything

Bracket notation property accessors in C#. 

## Usage

```
    IIndexed<Person> indexed = new Indexed<Person>(new Person());
    indexed["Name"] = "John Doe";
```

```
/// <returns>
///     [SectionName] 
///     Property1=value1
///     Property2=value2
///     ...
/// </returns>
public string GetAsIniSection(object obj, string sectionName)
{
    return this.GetAsIniSection(new Indexed(obj), sectionName);
}

public string GetAsIniSection(IIndexed indexed, string sectionName)
{
    StringBuilder sb = new StringBuilder();
    sb.Append("[");
    sb.Append(sectionName);
    sb.Append("]");

    foreach (string name in indexed.Keys)
    {
        sb.Append(name);
        sb.Append("=");
        sb.Append(indexed[name]);
        sb.Append(Environment.NewLine);
    }

    return sb.ToString();
}
```

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details