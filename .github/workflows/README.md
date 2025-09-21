# Cache Reset Workflow

## Overview

This workflow automatically resets GitHub Pages cache by temporarily switching between branches when you commit to `joeyaugust1-patch-3`.

## How It Works

1. **Trigger**: When you commit code changes to `joeyaugust1-patch-3`
2. **Switch to Branch 2**: Temporarily changes GitHub Pages source to `joeyaugust1-patch-2`
3. **Wait**: Brief pause to allow deployment to stabilize
4. **Switch Back**: Changes GitHub Pages source back to `joeyaugust1-patch-3`
5. **Result**: Fresh deployment with cache reset

## Branches Used

- **Branch 2**: `joeyaugust1-patch-2` (temporary switch target)
- **Branch 3**: `joeyaugust1-patch-3` (your working branch, final deployment target)

## Benefits

- **Automatic**: Runs every time you push to branch 3
- **Cache Reset**: Forces a fresh deployment to clear any cached content
- **Testing**: Allows you to test changes with a clean slate
- **No Manual Work**: No need to manually switch branches in GitHub Settings

## Manual Trigger

You can also manually trigger this workflow:
1. Go to Actions tab in your GitHub repository
2. Select "Reset Cache Branch Switch" workflow
3. Click "Run workflow" button

## Troubleshooting

If the workflow fails:
1. Check that both branches exist and are accessible
2. Ensure GitHub Pages is enabled in repository settings
3. Verify that the workflow has appropriate permissions

## Files

- `.github/workflows/reset-cache-branch-switch.yml` - Main workflow file
- This README documents the process