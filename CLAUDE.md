# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an Azure Data Factory (ADF) test repository exploring the feasibility of Claude Code connecting to data factories and building pipelines. The repository contains ADF configuration files and pipeline definitions in JSON format.

## Repository Structure

The codebase follows the standard Azure Data Factory ARM template structure:

- `main/` - Contains all ADF resource definitions
  - `factory/` - Data factory configuration (adf-concrnd.json)
  - `dataset/` - Dataset definitions for data sources and destinations
  - `linkedService/` - Connection configurations to external data stores (Azure Blob, SQL Server)
  - `integrationRuntime/` - Runtime configurations for data processing
  - `pipeline/` - Pipeline definitions containing data transformation activities
  - `publish_config.json` - Publishing configuration for ADF deployment

## Architecture

This is an Azure Data Factory project with the following key components:

- **Factory**: `adf-concrnd` located in East US region with system-assigned managed identity
- **Pipeline**: `CopyPipeline_g73` - A simple copy activity pipeline that moves data from one Azure Blob container to another
- **Datasets**: Binary datasets for source and destination files in Azure Blob Storage
- **Linked Services**: Connections to Azure Blob Storage and SQL Server databases
- **Integration Runtimes**: Managed runtimes for data processing (configured for Canada East region)

The main data flow copies CSV files between Azure Blob Storage containers using binary format processing.

## Development Notes

- This repository contains only configuration files - no build, test, or deployment scripts are present
- Files are managed through Azure Data Factory's Git integration
- The `publish_config.json` indicates this project uses the `adf_publish` branch for deployments
- All resources use the naming convention with `_g73` suffix or `Concrnd` identifier

## Security Considerations

- Linked services contain encrypted credentials for external connections
- The factory uses system-assigned managed identity for authentication
- Connection strings and sensitive data are properly encrypted using ADF's credential management