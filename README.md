# EC2 Private IP address to Hostname

This is a Bash script that takes a private IP address of an EC2 instance as input and returns the hostname and the link to the EC2 instance's detail page on the AWS Management Console.

## Requirements

- AWS CLI

## Usage

```bash
Usage: ./ec2-private-ip-to-hostname <private-ip-address>
       ./ec2-private-ip-to-hostname [-h | --help]

Options:
  -h, --help  Show this help message and usage.
```

`private-ip-address`: Required. The private IP address of the EC2 instance. Separators are supported for dots and hyphens.

## Example

```bash
$ ./ec2-private-ip-to-hostname 10.0.0.100
Instance Name: my-ec2-instance
Instance Link: https://console.aws.amazon.com/ec2/v2/home?region=us-east-1#InstanceDetails:instanceId=i-0123456789abcdefg
```

## Download

```bash
curl -o ec2-private-ip-to-hostname -L https://raw.githubusercontent.com/umi8/ec2-private-ip-to-hostname/main/ec2-private-ip-to-hostname
```

```bash
chmod u+x ec2-private-ip-to-hostname
```

## Setting up an AWS CLI alias

If you'd like to use this script with an AWS CLI alias, you can follow these steps:

Open your AWS CLI alias configuration file:
```bash
vi ~/.aws/cli/alias
```

Add the toplevel section to create an alias:
```bash
[toplevel]
show-hostname-from-private-ip = !/path/to/ec2-private-ip-to-hostname
```

Be sure to replace /path/to/ with the actual path to the script.
Save and close the configuration file.
You can now use the alias to invoke the script, like this:

```bash
aws show-hostname-from-private-ip <private-ip-address>
```
Note that you'll need to make sure the script is executable and located in a directory that's on your system's PATH in order for this to work. Also, by using the ! operator in the alias definition, you can run a shell command as an alias.
